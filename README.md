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
Весь файл https://github.com/pkostua/tf-hw-01/blob/master/task1_main.tf
### Результат запуска
![image](https://github.com/user-attachments/assets/5386b3c3-bcf0-4eb7-b6f3-cd77268a6dba)
### Применение  -auto-approve
Вы не можете оценить изменения при использовании -auto-approve, однако эта фича необходима при автоматизации сборки/деплоя 
### Переименованный контейнер
![image](https://github.com/user-attachments/assets/a65ccd6c-8d49-41dd-8535-dc3b5f2e56b5)
### После дестроя
![image](https://github.com/user-attachments/assets/4e9ec470-d6e9-4447-a777-3d13e9016815)
## Почему образ не удалился?
Судя по документации провайдера за удаление образа отвечают два свойства
1. keep_locally -  (Boolean) If true, then the Docker image won't be deleted on destroy operation. If this is false, it will delete the image from the docker local storage on destroy. Явно говорит нам о том, что образ не будет удален при destroy если оно выставлено в true. Что и сделано в нашем коде  keep_locally = true
2. force_remove - (Boolean) If true, then the image is removed forcibly when the resource is destroyed. Похоже, аналог keep_locally, только наоборот, но мы его не указывали - видимо подтянулось значение по умолчанию. Пойдем в консоль и посмотри  что там установлено
   ![image](https://github.com/user-attachments/assets/5c44d33c-4385-4315-9e4c-5c37b80c290e)
   Это явно не true, зачит удаление не произойдет

## Задание 2
Код который все делает https://github.com/pkostua/tf-hw-01/blob/master/task2_main.tf
![image](https://github.com/user-attachments/assets/e2774d8d-399a-4ae8-8e67-46e5925cd1a8)

