## Cấu trúc thư mục dự án (Directory Structure)

Dưới đây là cấu trúc thư mục tiêu chuẩn của dự án Ansible này:

```text
ansible-project/
├── ansible.cfg             # File cấu hình chung của Ansible
├── inventory/              # Chứa danh sách các máy chủ (hosts)
│   ├── production          # File chứa IP/Domain của môi trường thật
│   └── staging             # File chứa IP/Domain của môi trường test
├── group_vars/             # Biến dùng chung cho một NHÓM máy chủ
│   ├── all.yml             # Biến áp dụng cho toàn bộ server
│   └── webservers.yml      # Biến chỉ áp dụng cho nhóm [webservers]
├── host_vars/              # Biến dành riêng cho TỪNG máy chủ cụ thể
│   └── 192.168.1.10.yml    # Biến chỉ áp dụng cho IP này
├── site.yml                # Master Playbook (Kịch bản gốc gộp tất cả)
├── web-playbook.yml        # Playbook chạy riêng cho cụm Web
├── db-playbook.yml         # Playbook chạy riêng cho cụm Database
└── roles/                  # Thư mục chứa các "Gói công việc" (Roles)
    └── nginx_setup/        # Tên một role (ví dụ: cài đặt Nginx)
        ├── tasks/          # Chứa file main.yml (Các bước thực thi chính)
        ├── handlers/       # Chứa hành động kích hoạt sau (vd: restart service)
        ├── templates/      # Chứa file cấu hình mẫu (đuôi .j2 - Jinja2)
        ├── files/          # Chứa các file tĩnh (copy trực tiếp lên server)
        ├── vars/           # Biến nội bộ, ưu tiên cao của role này
        ├── defaults/       # Biến mặc định, ưu tiên thấp nhất của role
        └── meta/           # Khai báo thông tin tác giả, các role phụ thuộc
