# A web scraper running on AWS Lambda
This is an example of a web scraper running on AWS Lambda and Lambda Layers. It assumes, that you have [AWS CDK][cdk] and Docker installed. The docker image relies on [serverless-chrome][chromium].

### Create a CDK app enviroment

 	# Create a new directory with whatever you want to name your app
  	mkdir scraper-demo
   	cd scraper-demo
	cdk init --language python

 	python -m venv .venv
  	source .venv/bin/activate
   	pip install -r requirements.txt

### copy the files below to created app folder

	run.sh
	index.py
	app.py
	Dockerfile
	scraper_demo/scraper_demo_stack.py


### build the Docker image, the output will be stored in python/ folder

	docker build -t myapp .
	docker run -i -v `pwd`/python:/opt/ext -t myapp

### create a S3 bucket for the assets

	cdk bootstrap aws://your AWS ID/region

### deploy to AWS

	cdk deploy

### NOTE

Please note, that by default not the newest version of Chromium is used. If you have a concern about it please update the project accordingly.

[cdk]: https://aws.amazon.com/cdk/
[chromium]: https://github.com/adieuadieu/serverless-chrome/


## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.


