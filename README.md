[![Stories in Ready](https://badge.waffle.io/itodais/archive-of-learning.png?label=ready&title=Ready)](https://waffle.io/itodais/archive-of-learning)
# 勉強用リポジトリの集積所
Publicなら上限ないし、特にまとめる意味もない？

## 操作
- $ACCOUNT = githubのアカウント名
- $REPO = サブディレクトリに移したいレポジトリ名
- $ARCHIVE = 複数リポジトリをまとめておくアーカイブ用親リポジトリの名前

### まとめる

    git remote add $REPO git@github.com:$ACCOUNT/$REPO.git
    git fetch $REPO
    git checkout -b $REPO $REPO/master
    git filter-branch -f --tree-filter "mkdir $REPO && git mv -k {,.[\!.],..[\!.]}* $REPO/"
    git checkout master
    git merge $REPO

### きりだす

    git clone git@github.com:$ACCOUNT/$ARCHIVE.git $REPO
    cd $REPO
    git filter-branch --subdirectory-filter $REPO
    git remote add origin git@github.com:$ACCOUNT/$REPO.git
    git push -u origin master

### 参考
- http://qiita.com/awakia/items/6233eeac21fb895fa58d
