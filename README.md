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
![image](https://github.com/user-attachments/assets/5386b3c3-bcf0-4eb7-b6f3-cd77268a6dba)
### Применение  -auto-approve
Вы не можете оценить изменения при использовании -auto-approve, однако эта фича необходима при автоматизации сборки/деплоя
![image](https://github.com/user-attachments/assets/a65ccd6c-8d49-41dd-8535-dc3b5f2e56b5)
![image](https://github.com/user-attachments/assets/4e9ec470-d6e9-4447-a777-3d13e9016815)

