
- **Трябва да си генерирате ``ssh-key``, което става по следния начин:**
**На вашата виртуална машина или вашият компютър (трябва да има линукс) пишете следните команди които ще създат нещата необходими:**

Отваряте си конзолата на вашата машина виртуална или физическа и пишете:

``pwd`` --> с цел да видите в коя директория сте попринцип трябва да се във ``home/вашето-потребителско-име`` .

След това ползвате следните команди за да активирате вашият ``ssh агент`` --> ``eval `ssh-agent``.
Ще видите следното съобщение в резултат на изпълнената команда: 

``Agent pid 6171``

Което посочва, че вашият уред за съврзване с репоситорито работи.

След това изпълнете следните команди за да създадтете вашият ключ:

``ssh-keygen``

Което ще ви покаже следният изход от изпълнението си:

```
ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/$USER/.ssh/id_rsa): Път до мястото на съхранение/Препоръчва се /home/$USER/.ssh/
```

След като го съхраните ще трябва да използвате командата:

``ssh-add път/до/ключа/личният ключ``

След като го добавите ще видите подобен на моят резултат:

```
Identity added: /home/nick/.ssh/repo (nick@xmachine)
```

След това ще трябва да ми изпратите вашият ключ на моят nikolaykostov.nk@gmail.com или [messenger](https://www.messenger.com/t/nickkostov) (абе както се разберем на първият урок), но първо трябва да знаете, че тези ключове са два. Както посочвам от горе има личен и следователно публичен. Вие трябва да ползвате личният си за вашият компютър, а този който ще трябва да ми пратите е публичният. Публичните ключове изглеждат като този:

```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDWjekckSdrdesO+y8ravwmPR+xECKXW+fttw/3MFFqCnBPZc/cC8ayqhGuBq68i7GntYd6Qs5EcVguSNW6PobTY+MX0qVoUDKogQQP7QLu+vL7IDmryJKlTStgxqeUjcKykcJ4b+hqdosOy6WK04E/ABXS+QEeNRzMD/k1bevfeAAknqlMxSq9oC2wL3inVMdGtSqmowY+COMCQ4JEy+FkPubCk2sVBr/KsOZZgI5PWRIUEpUh2LBBecQHs4lbnYOZ8PhTr7BJhFzaZTC2o9F+cfJ5nFZ0giXh5RCoFT3CVQIK2Ir0x12lD2fi9htVzPxJcSMqzCbT2NyG43KM/GeTf8FGoeAthi4mUsSpLkbI8icD9A8lfN+E07pVwB26wIKHdr67Lu0ZRjYs9ZkXxUYfcYACxkurRKug3+Wh5mvQ1nqC7pl9DuWmpczkPFZwYCZMF7nurCYF9ORJtpTHLaHMYLywiFVi4jszhhAsjnvTedpVid5FuOsGx5ZdudkawGs= nick@xmachine
```

И за да може да го отворите ползвайте следното:

```
cat .ssh/Вашият–Публичен-Ключ.pub
```

След като вземете изхода на ключа директно ми го изпратете.


```bash
git clone git@github.com:nickkostov/LPIC.git
```
