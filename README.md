# 220601002_ros2_env

BYM412 Robotik Dersi – Ödev 1  
Ubuntu 22.04 üzerinde ROS 2 Humble ve Gazebo Harmonic kullanılarak TurtleBot4 simülasyon ortamının kurulması ve doğrulanması.

---

## Öğrenci Bilgileri
- **Ad Soyad:** Nisa Sumeyye Albayrak  
- **Öğrenci No:** 220601002  
- **Ders:** BYM412 – Robotik  
- **Dönem:** 2025 Güz  

---

## Sistem Bilgileri
- **İşletim Sistemi:** Ubuntu 22.04 LTS (Jammy)  
  *(Windows 11 ile dual-boot kurulumu)*  
- **ROS 2 Dağıtımı:** ROS 2 Humble Hawksbill  
- **Simülasyon Ortamı:** Gazebo Harmonic (gz-sim)  
- **Robot:** TurtleBot4 (simülasyon)

---

## Proje Özeti
Bu repoda, ROS 2 Humble ve Gazebo Harmonic kullanılarak TurtleBot4 robotunun simülasyon ortamında çalıştırılması, klavye ile kontrol edilmesi ve ROS 2 mimarisine ait temel bileşenlerin (node, topic, service, parametre) incelenmesi gerçekleştirilmiştir.

Simülasyon sırasında robot, `teleop_twist_keyboard` paketi aracılığıyla `/cmd_vel` topic’i üzerinden kontrol edilmiştir. Sensör ve durum verileri ROS 2 topic’leri kullanılarak gözlemlenmiştir.

---

## SSF (Student System Fingerprint) Doğrulaması
Ödev kapsamında öğrenciye ait sistem doğrulaması için SSF scripti çalıştırılmıştır. Script çalıştırılması sonucunda elde edilen SHA256 hash değeri aşağıda verilmiştir:
334ffe515978bac0887602d4009ce9d40d06e501c3ffb6190f132698e100bc14


- **SSF çıktı dosyası:** `SSF_HASH.txt`

---

## Kullanılan Temel ROS Bileşenleri

### Node’lar
- `teleop_twist_keyboard` – Klavye girdilerini hız komutlarına dönüştürür  
- `robot_state_publisher` – Robotun koordinat dönüşümlerini yayınlar  
- `diffdrive_controller` – Diferansiyel sürüş kontrolünü sağlar  
- Gazebo simülasyon node’ları – Fizik ve sensör simülasyonunu yönetir  

### Topic’ler
- `/cmd_vel` – Robot hız komutları  
- `/odom` – Odometri bilgisi  
- `/scan` – LIDAR sensör verisi  
- `/tf`, `/tf_static` – Koordinat dönüşümleri  
- `/joint_states` – Eklemlerin durumu  

---

## Simülasyonun Çalıştırılması

```bash
# TurtleBot4 simülasyonunu başlat
ros2 launch turtlebot4_ignition_bringup turtlebot4_ignition.launch.py

# Robotu klavye ile kontrol et
ros2 run teleop_twist_keyboard teleop_twist_keyboard

## Doğrulama Komutları

ros2 doctor --report
ros2 node list
ros2 topic list
ros2 topic echo /cmd_vel
ros2 topic echo /odom
gz --version

