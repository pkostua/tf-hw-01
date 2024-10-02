# Решение домашнего задания к занятию «Введение в Terraform»
https://github.com/netology-code/ter-homeworks/blob/main/01/hw-01.md
## Задание 1
![image](https://github.com/user-attachments/assets/9c65bda1-0662-40cf-818a-ff0a513541a9)
![image](https://github.com/user-attachments/assets/7a796320-309a-42d6-a293-404c561f6223)
Исправленный фрагмент кода
```
resource "docker_image" "nginx" {
  name         = "nginx:latest"
  keep_locally = true
}

resource "docker_container" "nginx" {
  image = docker_image.nginx.image_id
  name  = "example_${random_password.random_string.result}"

  ports {
    internal = 80
    external = 9090
  }
}
```

