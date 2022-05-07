pipeline {
    agent any
      environment {
        registry = "072669763386.dkr.ecr.eu-west-2.amazonaws.com/ecr-1"
    }
    stages{
        stage('checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/deepika2chebolu/aws-rds-java.git']]])
            }
        }
        stage('Docker Build') {
            steps {
                script {
                    dockerImage = docker.build registry
                }
            }
        }
        stage('Docker push') {
            steps {
                script {
                    sh 'aws ecr --region eu-west-2 | docker login -u AWS -p MIIEowIBAAKCAQEAvUR2bXxIr2rgp2WA4rY4mI0JD6AmalBGJtxQwGr+fqM17smd
NPcKnCAdlowknfjuOAHWatCFLPa4NDOTv6Vjxai2B1kG00swZn1Cz1A8TOKzsg+W
/40LoEXqnr7nxY/8dGKAj/V1tewaOvDgPVNY2O4ySROwKydgmZ2HFAMHeUYhZkJg
v7XjuzprFOJypN9bJ1l+rGloPTpoBZRExOe5B1NlcPAjKhqPfIVM6Ku1yKM+HmXQ
PlmFs4Gn3hvZJeM5qdtCQ/w02GRXgixnb8ELdpU9dFA3MbvJn8is32DMVnORdFSj
ZhBsjDmRQoTaMbOrPukIr/whMLjrSDRi5awAEQIDAQABAoIBACNF/SROg2Vd79yC
yFB4UXfs4QFugXpS16Aqc0pJJoEHfeew34GdgPaz7Y+/MpvWZt89SG7Dye4lVRM1
gZW4By4xUStxZho+6xhOxALLG1Hg9kh7K1MZQE9weFd5kMx7FzvBl+A8iOGMzR6r
Ab+sJuTXD7wa1TxVrGU0vJX4Mo5hNzYf42LGorP3AHouFhITRcPFaH66UPMbq/0U
XqRCthn3ipo5N6Cu1kGVPKNgGlDv2cuwe1nvynW7bkY5Gb6dia+a7Y7qHusHomXV
fh19DBzy2W4uiAifu1C31KFMuNm/Pb7yU+8E3Du6AzuXoj7LZ1Ajb9s6yQlt/ekF
df5V//kCgYEA8XXS6AeV/Q8PHRbboZh4tJrWD49dj1tmwRF6K2vjQoyVVFN7s6H6
szJIzJgvmwLqlBIIC1J5QtwY/l4jdEMkVHmecjsM2tZ7aSgvdSJg5OriAwBy3o6U
qOGdplqnYj1SjVjboIDig+qlIBd53FD/vAOQY56ZpctsAU7rCcpI8IMCgYEAyKoS
dpv/Ft3u7o9DuEVXRQXtsYKu4Jt5NawejFxM+awL+4gZz0buNWa1xMFmOrFjF4z3
4kxEGqaowZxSGgYur+1dG55MqsLvkPeFusfhergn9xElW9dDYfWlG4nEpUcyNqhn
OBqxgisnOQE7PndTWcIEQwFQ9EkxbcnDb+pMwNsCgYEA1cH6/lKI48iLFrN/qCU0
5p4UVx4SM7E03EK+puYSAH44TLjDUBlbuXwQmp83tcD1LjRwTqWqmBgFQFrShEBU
TzyDmpjQHoO2KTfcG5RdtwqBHysshf4vePqS+AxVFlE3Xc6GUCcJYMM/f5OI3BQQ
8b8t+iMT3oShjt7wkHA19kUCgYA9d3M+Z9yEuajV5Iae7Ial+wHrbRd6b8V6PmYB
IsjldeEZxH/7cUPIkdS+F2vkMLAk56aK6Ee4TjLFU8gGdrxYYYIy0pOzfxD5PAj3
xQB5oe2EDfl+n3rhh+hyfgoBgsSL35v2oJ6dO/DA0nK+WLjsdrTtfXq5ya3dbn9y
SbgHHwKBgF4YU9zVgFAzGj4FjQthaKRegQHJ8p+/zk1AjDXE2DnpWPImJGiJW0jX
eNQW/il4aHkIjZabtFhO/0snluaJzw86FHRsg/06FqVD0frnzc3Kurf2I+TO7xfx
uQr+NXm5hYtA4yenckx51ekL8yyNx8SGJotE0Y4gWnI6pokzSLFU
 072669763386.dkr.ecr.eu-west-2.amazonaws.com/ecr-1'
                    sh 'docker push 072669763386.dkr.ecr.eu-west-2.amazonaws.com/ecr-1:latest'
                }
            }
        }
    }
}    
