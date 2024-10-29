# new-Code

gcloud auth list

gcloud services enable compute.googleapis.com --project=$DEVSHELL_PROJECT_ID

gsutil mb gs://fancy-store-$DEVSHELL_PROJECT_ID

git clone https://github.com/googlecodelabs/monolith-to-microservices.git
cd ~/monolith-to-microservices
./setup.sh
nvm install --lts

curl -LO raw.githubusercontent.com/Techcps/GSP-Short-Trick/master/Hosting%20a%20Web%20App%20on%20Google%20Cloud%20Using%20Compute%20Engine/startup-script.sh

gsutil cp ~/monolith-to-microservices/startup-script.sh gs://fancy-store-$DEVSHELL_PROJECT_ID

cd ~
rm -rf monolith-to-microservices/*/node_modules
gsutil -m cp -r monolith-to-microservices gs://fancy-store-$DEVSHELL_PROJECT_ID/

gcloud compute instances create backend --zone=$ZONE --machine-type=e2-standard-2 --tags=backend --metadata=startup-script-url=https://
