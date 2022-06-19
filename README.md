## ADCP - Terraform Visualizer

ADCP - Terraform Visualizer is a [Terraform](http://terraform.io/) visualizer. 

In order to do this, ADCP - Terraform Visualizer:

1. generates a [`plan`](https://www.terraform.io/docs/cli/commands/plan.html#out-filename) file and parses the configuration in the root directory or uses a provided plan.
1. parses the `plan` and configuration files to generate three items: the resource overview (`rso`), the resource map (`map`), and the resource graph (`graph`).
1. consumes the `rso`, `map`, and `graph` to generate an interactive configuration and state visualization hosts on `0.0.0.0:9000`.

Feedback (via issues) and pull requests are appreciated! 

![Rover Screenshot](docs/rover-cropped-screenshot.png)

## Quickstart

The fastest way to get up and running with ADCP - Terraform Visualizer is through Docker.

Follow the Steps: 

Step 1: Configure your environment variables by exporting your credentials as shown below

export AWS_ACCESS_KEY_ID=AKIAIOSFODNN7EXAMPLE
export AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
export AWS_DEFAULT_REGION=us-west-2

Step 2: Use `--env` or `--env-file` to set environment variables in the Docker container. For example, you can save your AWS credentials to a `.env` file.

```
$ printenv | grep "AWS" > .env
```

Then, add it as environment variables to your Docker container with `--env-file`.

```
$ docker run --rm -it -p 9000:9000 -v $(pwd):/src --env-file ./.env KashDC/Terraform_Visualisation
2021/07/02 06:46:23 Starting Rover...
2021/07/02 06:46:23 Initializing Terraform...
2021/07/02 06:46:24 Generating plan...
2021/07/02 06:46:25 Parsing configuration...
2021/07/02 06:46:25 Generating resource overview...
2021/07/02 06:46:25 Generating resource map...
2021/07/02 06:46:25 Generating resource graph...
2021/07/02 06:46:25 Done generating assets.
2021/07/02 06:46:25 Rover is running on 0.0.0.0:9000
```

Once Rover runs on `0.0.0.0:9000`, navigate to it to find the visualization!

