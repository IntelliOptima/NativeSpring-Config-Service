# Build
custom_build(
    # Name of the target
    ref= 'config-service',
    # Command to build the container image
    command= 'gradle bootBuildImage --imageName %EXPECTED_REF%',
    # Files to watch for changes to trigger a rebuild
    deps = ['build.gradle', 'src'],

    #Hot Reload
    live_update=[
        #Sync changed files to the container
        sync('./src', '/workspace/src'),
    ]
)

# Deploy
k8s_yaml(kustomize('./k8s/resources/base'))

# Manage
k8s_resource('config-service', port_forwards=['8888'])