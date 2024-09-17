# some example

steps {
                
                // container(name: 'kaniko', shell: '/busybox/sh') {

                container('kaniko') {
                    
                    // def TOK="aaaaaaa"
                    // sh "echo $TOK"
                    
                    sh '''
                    
                        DIR=\"$(pwd)/repo\"
                        
                        echo $DIR
                        
                        ls -l 
                        
                        cd repo && ls -l .
                        
                        DOCFILE=Dockerfile
                        
                        cat $DOCFILE
                    
                        
                        CI_REGISTRY=\"registry.local.homelabsolutions.net/afsas/fips-spring-java\"
                    
                        CI_REGISTRY_BASE64_TOKEN=\"========\"
                        
                        echo '{"auths": { "registry.local.homelabsolutions.net": { "auth": "Z2l0bGFiX3VzZXI6TjFramVOVV9OZllidkNzY3FfdVE=" }}}' >/kaniko/.docker/config.json
                        
                        cat /kaniko/.docker/config.json
                        
                        /kaniko/executor -f \"$DOCFILE\" -c . --insecure --skip-tls-verify --cache=true --destination=\"$CI_REGISTRY\"
                        
                    '''
    
                }
            
