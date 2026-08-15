1) create a new repo on github

meta-yocto

1.1) clone locally

git clone git@github.com:RobertBerger/meta-yocto.git

2) add my-scripts dir

cd meta-yocto

echo "# meta-yocto fork" >> README.md

git init

git add .

git commit -m "first commit"

git remote add origin git@github.com:RobertBerger/meta-yocto.git

git push -u origin master

3) use my repo

mv meta-yocto meta-yocto.ori
git clone git@github.com:RobertBerger/meta-yocto.git

4) add upstream

cd meta-yocto

git remote add official-upstream https://git.yoctoproject.org/meta-yocto

$ git fetch official-upstream

$ git branch -a
* master
  remotes/official-upstream/bernard
  remotes/official-upstream/contrib/abelloni/master-next
  remotes/official-upstream/contrib/abelloni/master-next-success
  remotes/official-upstream/contrib/agodard/master-next
  remotes/official-upstream/contrib/agodard/master-next-success
  remotes/official-upstream/contrib/dunfell-next
  remotes/official-upstream/contrib/hardknott-next
  remotes/official-upstream/contrib/honister-next
  remotes/official-upstream/contrib/kirkstone-next
  remotes/official-upstream/contrib/langdale-next
  remotes/official-upstream/contrib/lucaceresoli/master-next
  remotes/official-upstream/contrib/lucaceresoli/master-next-success
  remotes/official-upstream/contrib/mathieu/master-next
  remotes/official-upstream/contrib/mathieu/master-next-success
  remotes/official-upstream/contrib/mathieu/test
  remotes/official-upstream/contrib/mickledore-next
  remotes/official-upstream/contrib/nanbield-next
  remotes/official-upstream/contrib/scarthgap-next
  remotes/official-upstream/contrib/styhead-next
  remotes/official-upstream/contrib/walnascar-next
  remotes/official-upstream/daisy
  remotes/official-upstream/danny
  remotes/official-upstream/denzil
  remotes/official-upstream/dizzy
  remotes/official-upstream/dora
  remotes/official-upstream/dunfell
  remotes/official-upstream/dylan
  remotes/official-upstream/edison
  remotes/official-upstream/fido
  remotes/official-upstream/gatesgarth
  remotes/official-upstream/hardknott
  remotes/official-upstream/honister
  remotes/official-upstream/jethro
  remotes/official-upstream/kirkstone
  remotes/official-upstream/krogoth
  remotes/official-upstream/langdale
  remotes/official-upstream/master
  remotes/official-upstream/master-next
  remotes/official-upstream/master-next2
  remotes/official-upstream/mickledore

...

$ git tag -l
5.3_M3
6.0_M1
6.0_M2
daisy-11.0.0
danny-8.0
danny-8.0.1
danny-8.0.2
denzil-7.0
denzil-7.0.0
denzil-7.0.1
denzil-7.0.2
dizzy-12.0.2
dunfell-23.0.8
edison-6.0
edison-6.0.1
edison-6.0.2
fido-13.0.0
hardknott-3.3
hardknott-3.3.1
yocto-1.0
yocto-1.1
yocto-1.1.1
yocto-1.1.2
yocto-1.2
yocto-1.4
yocto-1.4.1
yocto-1.4.2
yocto-1.4.2.rc1
yocto-1.4.3
yocto-1.4.4
yocto-1.5
yocto-1.5.1

...

5) use the master branch on a specific commit, apply patches and make own branch

git co official-upstream/master

git co a67ae0e83d8aba0c46cb8383808b2d1203fbb414

5.1) create branch
git branch 2026-08-11-training

5.2) checkout branch
git co 2026-08-11-training

5.3)
let's set a tag to mark the last official upstream changes
git tag meta-yocto-a67ae0e83d8aba0c46cb8383808b2d1203fbb414

5.4) patch/add/commit




#5) use specific upstream branch/commit and make own branch
#
#syntax: git fetch url-to-repo branchname:refs/remotes/origin/branchname
#
#$ git fetch git://github.com/STMicroelectronics/meta-st-stm32mp dunfell:refs/remotes/origin/dunfell
#
#From git://github.com/Freescale/meta-freescale
# * [new branch]        dunfell    -> origin/dunfell
#

#6) Update from upstream:
#git co master
#>> git remote -v
#
#official-upstream       git://github.com/Freescale/meta-freescale (fetch)
#official-upstream       git://github.com/Freescale/meta-freescale (push)
#origin  git@github.com:RobertBerger/meta-freescale.git (fetch)
#origin  git@github.com:RobertBerger/meta-freescale.git (push)
#
#>> git fetch official-upstream
#remote: Counting objects: 4043, done.
#remote: Compressing objects: 100% (1273/1273), done.
#remote: Total 4043 (delta 3130), reused 3632 (delta 2727)
#Receiving objects: 100% (4043/4043), 721.50 KiB | 402.00 KiB/s, done.
#Resolving deltas: 100% (3130/3130), completed with 502 local objects.
#From git://git://github.com/Freescale/meta-freescale
#   62591d9..e758547  master     -> official-upstream/master
# + 2942327...a382678 master-next -> official-upstream/master-next  (forced update)
#   a3fa5ce..6a1f33c  morty      -> official-upstream/morty
#---
#

6) hack the branch and update

6.1) hack it

6.2) add/commit

6.3) What was changed?

$ git diff 2021-06-09-3ba7567532bcda55d9d73deff80a350877b68d07-pd21.1.0-stm-dunfell --stat
 conf/layer.conf                                                           | 2 +-
 recipes-bsp/u-boot/{u-boot_2020.01.bbappend => u-boot_2020.01.bbbbappend} | 0
 2 files changed, 1 insertion(+), 1 deletion(-)

7) push upstream:
git co master
cd my-scripts
./push-all-to-github.sh

#8) apply patches
#
#cd meta-virtualization
#
#git co 2019-09-09-warrior-2.7+
#
#stg init
#
#stg series
#
#stg import --mail ../meta-virtualization-patches/2019-09-09-warrior-2.7+/0001-use-systemd-as-cgroup-manager-for-docker-While-it-s-.patch
#
#import all patches
#
#...
#
#stg series
#
#stg commit --all
#
#git log
#
#git co master
#
9) push to my upstream

my-scripts/push-all-to-github.sh

