# ter-homeworks/01
![Terraform version](https://github.com/user-attachments/assets/4f8d484d-60e3-4a07-9af3-2fb54769c0e8)
![Docker version](https://github.com/user-attachments/assets/adb86a2c-032d-4715-a1c1-d7aaf93ff5bf)

## Задание 1
2. Допустимое хранение в personal.auto.tfvars
3. Sensitive data:
 
![Sensitive](https://github.com/user-attachments/assets/70ee80dd-7591-4e35-a723-8fb915a40ce2)

Key:value:

![Result](https://github.com/user-attachments/assets/bc7a1e06-f47b-4d00-914a-9beee420a31a)

4. Ошибки:
   
![Error](https://github.com/user-attachments/assets/7fae13a0-c09b-46fc-bf43-da998c903875)

   - для типа объекта "docker_image" отсутствует его уникальное имя
   - для типа объекта "docker_container" его уникальное имя должно начинаться с буквы или символа подчёркивания и содержать только буквы, цифры, символы подчёркивания и тире

![Error_1](https://github.com/user-attachments/assets/c1f7ed3c-89f3-44b6-8d64-3d77174debe9)
     
   - объекта с типом "random_password" и уникальным именем "random_string_FAKE" не декларировался
   - параметр "resulT". Имена параметров чувствительны к регистру.

5. main.tf:

```terraform
terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 3.0.1"
    }
  }
  required_version = ">=1.8.4"
}
provider "docker" {}

resource "random_password" "random_string" {
  length      = 16
  special     = false
  min_upper   = 1
  min_lower   = 1
  min_numeric = 1
}

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
![Docker_ps](https://github.com/user-attachments/assets/8b1013dd-b91d-4153-82c9-45b41434a305)

6. Ключ auto-approve - автоматическое утверждение операций Terraform. Он позволяет пропустить проверку изменений перед их применением, что может привести к непреднамеренным изменениям в инфраструктуре, в частности - при ошибке пользователя. 
Если действие происходит в рабочей (тестовой) среде и мы уверены, что изменения конфигураций релевантны, то применение ключа auto-approve позволит внедрить, например - автоматизированное тестирование для проверки конфигураций Terraform.

![Docker_ps_1](https://github.com/user-attachments/assets/4c679032-269f-4418-b790-6dd39533c19f)

7. State после terraform destoy:

![state_after_destroy](https://github.com/user-attachments/assets/092c78e6-e453-4d7b-87b5-ba6cc64982d1)

8. Параметр "keep_locally":

![Docker_image](https://github.com/user-attachments/assets/b089224b-28ad-4c52-9c17-8381ba75ab41)

![Keep_locally](https://github.com/user-attachments/assets/6c000e13-9698-4186-9402-26b35daa0929)

Если значение равно true, то образ Docker не будет удалён при операции уничтожения. Если значение равно false, то при операции уничтожения образ будет удалён из локального хранилища Docker.





