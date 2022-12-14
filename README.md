## Creating a CI/CD Pipeline for a static blog webpage built on Next.js, Markdown, and TypeScript, with Github action, AWS ECR and ECS


The source code was forked from the main source code repo 
- The orignal source code - https://github.com/vercel/next.js/tree/canary/examples/blog-starter

The main source code for the project was in /examples/blog-starter

I forked that into my github repo and started work.

## Steps
- Cloned the entire repo on my local PC
- Copied out /example/blog-starter
- Ran it locally on my PC with nodejs and npm installed to be sure it works and the source code is not broken
- made a multi-stage  [Dockerfile](./Dockerfile) to create an image out of the source code.
- Decided to use github actions as it is faster for the CI/CD workflow
- built my [github-actions](/.github/workflows/deploy_to_ecr_ecs.yml) workflow to store artifact in ECR and deploy in ECS
- created a repo on ECR on AWS Account in us-east-1 region 
- created ECS Cluster in same region
- My ECS cluster ran some EC2 Instances and used Auto scaling group for the EC2
- Attached a load balancer to the EC2 and connected it with Auto-Scaling Group
- Set up my AWS DNS route 53 and connect with my loadbalancer end point through A-records
- I made my setup highly available by spreading the cluster in different availability zone
- Used terraform (IAC) to set up VPCs, Subnets, Route tables, Internet Gateways etc
- Ran my github action workflow to build the image from the dockerfile, send it to ECR and deploy to ECS
- There are many other options for the architecture of this project but i decided to go with this.
- I could use fargate for my ECS rather than EC2 instances, then i dont have to worry about ASG
- other options like using AWS Apps runner, AWS Amplify etc. 


### Tools used

- docker
- [Dockerfile](./Dockerfile)
- [Github Actions](/.github/workflows/deploy_to_ecr_ecs.yml)
- AWS
- Elastic Container Registry 
- Elastic Container Services (EC2)
- [Terraform](./vpc.tf)

![image](https://user-images.githubusercontent.com/20236706/206466705-678b9199-d6b7-466e-a788-5511262247aa.png)

## Note
- This is just a summary of the project, it can be more elaborate but just keeping it simple. it is just a blog.



                          - Designed by 

                                - Nelson Nwajie
                                - Cloud DevOps Engineer
                                - 8th December 2022
