#open-assistant custom readme

sudo apt-get install docker-compose

sudo docker compose --profile inference build

sudo docker compose --profile inference up -d

sudo docker compose logs -f    \
    inference-server      \
    inference-worker      \
    inference-safety

#create venv
cd inference/text-client
python3 -m venv open_assistant_1
source open_assistant_1/bin/activate
pip3 install --user -r requirements.txt
PYTHONPATH=$PWD/../../oasst-shared python3 __main__.py
#You'll soon see a `User:` prompt, where you can type your prompts.


