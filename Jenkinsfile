apiVersion: v1

kind: BuildConfig

metadata:

  name: myfirstpipeline

  labels:

    name: myfirstpipeline

  annotations:

    pipeline.alpha.openshift.io/uses: '[{"name": "${NAME}", "namespace": "", "kind": "DeploymentConfig"}]'

spec:

  triggers:

    -

      type: GitHub

      github:

        secret: secret101

    -

      type: Generic

      generic:

        secret: secret101

  runPolicy: Serial

  source:

    type: None

  strategy:

    type: JenkinsPipeline

    jenkinsPipelineStrategy:

      jenkinsfile: "node {\nstage 'build'\nopenshiftBuild(buildConfig: '${NAME}', showBuildLogs: 'true')\nstage 'deploy'\nopenshiftDeploy(deploymentConfig: '${NAME}')\nopenshiftScale(deploymentConfig: ''${NAME}',replicaCount: '2')\n}"

  output:

  resources:

  postCommit:
