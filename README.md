# 🤖 RL-Gazebo-ROS2 Framework

Một framework mô-đun, hỗ trợ ROS 2, dùng để huấn luyện các agent học tăng cường (Reinforcement Learning - RL) trực tiếp trên Gazebo — hướng đến tính thực tế, dễ mở rộng, và phục vụ các bài toán robot thực tế.

---

## 🚨 Động cơ phát triển

Phần lớn các framework RL hiện nay như **Gym**, **Gymnasium**, **Isaac Gym**, hay **MuJoCo** đều được thiết kế cho môi trường mô phỏng riêng biệt, **không phải Gazebo**.

### ❓ Vậy tại sao nên huấn luyện RL trên Gazebo?

#### Ưu điểm:
- 🎯 **Mô phỏng vật lý chính xác cao** — phù hợp với robot thực tế.
- 🤖 **Tích hợp trực tiếp với ROS 2** — giảm thiểu rào cản triển khai thực.
- 🧩 **Hỗ trợ đa dạng cảm biến** — dễ dàng tích hợp LiDAR, camera, IMU...
- 📦 **Cài đặt phổ biến và dễ dùng** — vốn là tiêu chuẩn trong cộng đồng robot.

---

### ❌ Vì sao Gazebo chưa được dùng rộng rãi trong RL?

- 🐢 **Tốc độ huấn luyện chậm** — do mô phỏng vật lý chính xác.
- 🧵 **Không hỗ trợ huấn luyện đa luồng** — tốn thời gian, tài nguyên.
- 🔄 **Phải truyền dữ liệu qua ROS** — thêm độ trễ, giảm hiệu suất.

> Rất nhiều nhóm nghiên cứu từng dùng Gazebo, nhưng:
> - Mỗi nơi tự dựng framework riêng, ít công bố mã nguồn.
> - Nếu có công bố thì thường chỉ hỗ trợ ROS 1 và không được duy trì.

---

## 💡 Mục tiêu dự án

Xây dựng một **framework RL đơn giản, rõ ràng, hỗ trợ ROS 2**, giúp các bạn đam mê robot dễ dàng:
- Bắt đầu với RL trên môi trường mô phỏng thực tế.
- Tiết kiệm thời gian thiết lập hạ tầng.
- Tập trung vào thuật toán, không mất công build lại từ đầu.
![Screenshot from 2025-03-31 21-39-58](https://github.com/user-attachments/assets/542ca3be-7b6d-433a-b8f2-d06ec47f6d25)

---

## 🛠️ Hướng dẫn cài đặt & sử dụng

### 1. Clone repository
```bash
git clone [<link-repo>](https://github.com/phamduyaaaa/ros2-rl-framework.git)
```
### 2. Di chuyển vào thư mục src trong workspace ROS 2 của bạn:
```bash
cd <ten_workspace>/src
```
### 3. Thiết lập môi trường ROS:
```bash
source ../setup.bash
```
### 4. Build lại workspace:
```bash
colcon build
```
### 5. Xuất bản điểm đích (goal):
```bash
ros2 topic pub /goal_pose geometry_msgs/msg/Pose \
"{position: {x: 1.0, y: 2.0, z: 0.0}, orientation: {x: 0.0, y: 0.0, z: 0.0, w: 1.0}}"
```
### 6. Chạy server huấn luyện:
```bash
ros2 run rl_training train_server
```
### 7. Chạy node cung cấp thông tin môi trường:
```bash
ros2 run env_info env_info_node
```
### 8. Khởi động client huấn luyện:
```bash
ros2 run rl_training train_client
```
