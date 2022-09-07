# jenkins-git

A simple project to test jenkins git integration
And it should be triggered by any change 
By RK


https://s3.us-west-1.amazonaws.com/cloudformation-templates-us-west-1/LAMP_Multi_AZ.template

https://github.com/tongueroo/cloudformation-examples/blob/master/templates/single-instance.yml#L361-L378



Deployment Release Process 

Methods we have 

	*Single pipeline to Deploy in to multiple environments by passing variable parameters

		1. Simple deployment with variables as parameters to pipeline
		
		2. There is no authorisation for deployment

	Deployment Approvals
		
		1. Review and Authorise the deployment to certain protected environments
		2. We can add count for no of approvals required for Deployment
		
		1. We need to wait until deployment is reviewed and approved
		


	10 markets - 10 pipelines

	
		1. This is more precised and no dependency.
		2. Isolated Deployments with respect to each MRT
		
		1. We need to manage multiple pipelines
