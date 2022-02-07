# Git Daily Use

Setiap command dibawah mempunyai tambahan argumen masing2 yang bisa dimasukan 

## git Config

Sebelum kita dapat berinteraksi dengan **git source controll**, kita harus terlebih dahulu harus mengkonfigurasi agar git dapat dikenali

```
$ git config --global user.name "uchanz"
$ git config --global user.email ruslan.haris@gmail.com
```

untuk mengecek konfigurasi exiting, bisa kita lakukan dengan perintah sbb: 

`$ git config --list --show-origin`

## git init

Sekarang konfigurasi sudah di set, kita dapat menginistialisasi git repository kita. dimana hal ini akan membuat kita dapat mentrace *keep track* setiap perubahan local. tapi hal ini belum sampai diremote repository itu sendiri 

```
$ cd path/to/new/project
$ git init
Initialized empty Git repository in path/to/new/project/.git/
```

## git clone

jika kita tidak melakukan initialisasi git pada local repository kita maka hal lain yang bisa digunakan adalah **clone** dari remote repository dan untuk aktivity ini terdapat 2 protocol yang bisa digunakan yaitu :
- Hyper Text Transfer Protocol Secure (HTTPS)
- Secure Shell (SSH)

```
$ git clone https://github.com/tensorflow/tensorflow.git
$ git clone git@github.com:tensorflow/tensorflow.git
```

note : *Https adalah cara yang cepat dan mudah untuk melakukan clone repository, tetapi kita akan diminta untuk manual memasukan password setiap kali, sedangkan cloning menggunakan SSH membutuhkan setting up private key pair dengan **Github** tetapi lebih aman dan menghindari memasukan password 

## git status

Ketika kita menginitialisasi sebuah git local repository atau sekedar mengclone dari remote repository, kita dapat menggunakan perintah `$ git status` untuk mengecek state dari workspace kita. perintah ini memungkinkan kita dapat mengetahui jika ada perubahan yang belum tersimpan dan local repo kita lebih lama daripada remote repository 

```
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
 (use "git push" to publish your **local** commits)

Untracked files:
 (use "git add &lt;file&gt;..." to include **in** what will be committed)

	README.txt

nothing added to commit but untracked files present (use "git add" to track)
```

## git fetch

Setiap kali sebelum dimulai pekerjaan, biasakan untuk melakukan fetch (mengecek update local repo) dengan menggunkan perintah `git fetc` command ini akan meretrive brach dan update ke repository local, tapi perintah tersebut tidak akan merubah local workspace, perintah untuk melakukan hal tersebut adalah `git pull`

```
$ git fetch
remote: Counting objects: 43, done.
remote: Compressing objects: 100% (36/36), done.
remote: Total 43 (delta 10), reused 31 (delta 5)
Unpacking objects: 100% (43/43), done.
From https://github.com/some/repository
 * [new branch] master -&gt; master
 * [new branch] feature -&gt; feature
```

## git pull
## git add
## git commit 
## git push 
## git diff
## git rm 
## git branch
## git checkout
## git merge
## git log
## git show 
## git stash
## git reset 
## git remote
## git clean
