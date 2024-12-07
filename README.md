# Devops-Monitoring

Grafana - monitor, logs, alerts, metrices.
Prometheus stores the metrices, time-series database > capturing logs - Loki (open-source)tool and gives the logs to Grafana.Loki stores data.
Logs can be captured via promtail(collects from everywhere) > gives to Loki > Loki gives to Grafana.

Create an instance > connect to the instance.

sudo apt update
https://www.cherryservers.com/blog/install-grafana-ubuntu
- installing grafana into ubuntu

stable release copy key(signing key) enter > sudo apt update > sudo apt-get install grafana
To start Grafana: sudo systemctl start grafana-server
                  sudo systemctl enable grafana-server

Need to enable SG > port 3000 > source:myIP > take public IP:3000
GRAFANA WORKS!!!!
username: admin
password: admin

Add DB> loki > https://docs.google.com/document/d/1kHhk2LYss_c2pbBCCSXo4sqaqwNF3bj_MIiqm8L5b1U/edit?tab=t.0 (using docker)sudo apt-get install docker.io > docker ps > current ubuntu user to docker : sudo usermod -aG docker $USER > sudo reboot > docker ps >
mkdir grafana_configs > will create loki and promtail config > Install Loki > downloased loki configuration , download promtail configuration > ls > vim loki-config.yaml it works on port 3100 > run loki docker conatiner install > edit 3100 port > public IP:3100/ready > Install Promtail Config > docker ps -a > Go to Grafana welcome page > add datastore > we will need to add the loki url :http://public ip:3100/ > donot type public ip it should be localhost > test will be successful > explore > label:we will get the job name from promtail config.yaml >select value: varlogs > run query > 
cd > cd /var/ > ls > cd lig > ls > sudo cat grafana.logs
it should be shown in grafana > pwd > cd > cd grafana_configs > vim promtail-config.yaml > add new target > targets: localhost , labels: job: grafanalogs > --path__: /var/log/grafana/*log
docker restart promtail container > loki captured grafana logs > run query > lohgs I want to show in grafana dashboard > add to dashboard > add: visualisation > Install nginx to see the graph: sudo apt-get install nginx > logs generated > label: job , varlogs , line constraints:nginx 







