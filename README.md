# IoT-PBI
Push (IoT) button infrastructure

IoT-PBI - turn up a complete Rube Goldberg contraption stack using AWS IoT button.

# Brain dump #1

IoT push x1 -> spins up rpi ( how? )
               kicks off an ansible run
                builds 2 small vps ( ansible or Terraform )
                    installs on vps 1
                        supervisor
                            vpn server
                    installs on vps 2
                        supervisor
                            flask app    
                    starts on vps
                        vpn
                        supervisor
                           starts flask app
               route 53 adds dns
               installs on rpi 
                    supervisor
                    flask
                    slackclient
                    vpn client
                    qhue
               starts on rpi 
                    supervisor
                        vpn client
                        flask app
                            slack client
                            qhue

Front End VPS -> accepts connections to turn lights off / on
                 maintains SQS queue
                 reports to slack

Backend rpi -> handles qhue library requests
               reports to slack

IoT push x2 -> Reprts to slack
               tears down infratsructure


          
   
