terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = ">= 3.0, < 4.0"  # Compatible with all 3.x versions
    }
  }
}

provider "docker" {
  host = "npipe:////./pipe/docker_engine"  # For Windows named pipe access
}

resource "docker_image" "web_server_image" {
  name = "nginx:latest"
}

resource "docker_container" "web_server_container" {
  name  = "custom-nginx"
  image = docker_image.web_server_image.name

  ports {
    internal = 80
    external = 8081
  }
}
