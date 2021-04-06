# Chat-app

"Chat-appはSlackをイメージしたチャットアプリです。"

# DEMO

You can learn how to making cute physics simulations (looks retro game).

https://www.dropbox.com/s/z4dz46ybtn7ohch/%E7%AD%8B%E3%83%88%E3%83%AC%E6%84%9B%E5%A5%BD%E4%BC%9AGIF.gif?dl=0

This animation is a "Cat playing on trampoline"!
You can get basic skills for making physics simulations.

# Features

Physics_Sim_Py used [pyxel](https://github.com/kitao/pyxel) only.

```python
import pyxel
```
[Pyxel](https://github.com/kitao/pyxel) is a retro game engine for Python.
You can feel free to enjoy making pixel art style physics simulations.

# Requirement

* Ruby on rails 
* pyxel 1.0.2

Environments under [Anaconda for Windows](https://www.anaconda.com/distribution/) is tested.

```bash
conda create -n pyxel pip python=3.6 Anaconda
activate pyxel
```

# Installation

Install Pyxel with pip command.

```bash
pip install pyxel
```

# Usage

Please create python code named "demo.py".
And copy &amp; paste [Day4 tutorial code](https://cpp-learning.com/pyxel_physical_sim4/).

Run "demo.py"

```bash
python demo.py
```

# Note

I don't test environments under Linux and Mac.

# Author

* Hayabusa
* R&D Center
* Twitter : https://twitter.com/Cpp_Learning

# License

"Physics_Sim_Py" is under [MIT license](https://en.wikipedia.org/wiki/MIT_License).

Enjoy making cute physics simulations!

Thank you!

# テーブル設計

## users テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| name     | string | null: false |
| email    | string | null: false |
| password | string | null: false |

### Association

- has_many :room_users
- has_many :rooms, through: room_users
- has_many :messages

## rooms テーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| name   | string | null: false |

### Association

- has_many :room_users
- has_many :users, through: room_users
- has_many :messages

## room_users テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user

## messages テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user
