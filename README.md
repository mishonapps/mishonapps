# About
This repository contains upto date source code af all the cron jobs and applications that are accessible in https://www.mishon-apps.ca/

All the mishonapps resources were managed by **_it@mishon.ca_**

## Server info
We are using t3.xlarge (16GM RAM and 4vCPUs) AWS EC2 Instance to host mishon-apps.ca. It is a reserved instance with 3 years commitment (Started Feb 19th, 2022)

## Domain info
mishon-apps.ca domain is hosted using AWS Route53 (Will be billed annualy $14 USD for auto Renewal)

## MySQL Database
Most of the applicaions data is stored MySql Database hosted in AWS RDS Mysql Instance (bwmishondb). It is a t3.medium instance with two year commitment (Started Feb 19th, 2022)

## MongoDB
It is hosted inside EC2 instance and used only to store Picking and Packing data, However both applications were forefeited

## Dockerhub
All the Cronjobs and applications were dockerized and stored in a private repo (mishondocker).

## .Renviron file
This file is used to load all the credentials to R environment. It is a common file used by all the docker images using volume mount

# Steps for debugging R code

**Requirements**

1) Intermediate knowledge of R (Must be able to uderstand packages such bas dplyr, glue, data.table, stringr, DBI .....)
2) Download and Install latest version of R https://cran.r-project.org/bin/windows/base/
3) Download IDE https://posit.co/downloads/
4) Ping arunkodati@mishon.ca for a .Renviron file

# Steps for Deployement 

1) Build a docker image (Every application has it's own dockerfile in their respective repository)
2) Push the docker image to mishondocker private repository
3) In AWS EC2 Instance, navigate to /root/cron-docker and stop all cron jobs (docker-compose down)
4) In AWS EC2 Instance, Remove the images you want to deploy from docker (docker images)
5) In AWS EC2 Instance, start all cron jobs (docker-compose up -d)

In AWS EC2 Instance, Docker container configurations were managed using docker-compose.yml file located in /root/cron-docker

