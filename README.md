Build the image:

```console
% PROJECT=$(basename `pwd`)
% docker image build -t $PROJECT-image . --build-arg user_id=`id -u` --build-arg group_id=`id -g`
```

Run docker containers:

```console
% docker container run -it --rm --init --mount type=bind,src=`pwd`,dst=/app --name $PROJECT-container $PROJECT-image /bin/zsh
```

Run the following commands inside the Docker containers:

```console
% cd /app
% poetry install
% poetry run pytest
% poetry run ruff check prime.py
% poetry run invoke -l
```
