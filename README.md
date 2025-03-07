# Lucrare 3: Prima aplicație Docker

> Realizat de studentul: Badia Victor \
> Grupa: I2301
> \
> Verificat de Mihail Croitor

## Scopul Lucrării

Aceasta lucrare de laborator familiarizează cu elementele de bază ale containerizării și pregătește spațiul de lucru pentru următoarele lucrări de laborator.

## Sarcina

Instalarea Docker Desktop și verificarea funcționării acestuia.

## Pregătire

Descărcăm și instalăm Docker Desktop.

![1](https://github.com/user-attachments/assets/c54a3b3b-2838-4f28-8536-97080b3d7e2c)

## Executare

Creăm un repozitoriu containers03:

![2](https://github.com/user-attachments/assets/c6cc6aaa-a38e-4928-a703-752b23a7b301)

Clonăm repozitoriul pe calculator:

```bash
git clone https://github.com/viteok69/containers03-
```

Creăm în directorul containers03 fișierul Dockerfile cu următorul conținut:

```bash
FROM debian:latest
COPY ./site/ /var/www/html/
CMD ["sh", "-c", "echo hello from $HOSTNAME"]
```

cu ajutorul comenzii:

```bash
'FROM debian:latest`nCOPY ./site/ /var/www/html/`nCMD ["sh", "-c", "echo hello from $HOSTNAME"]' | Out-File -FilePath Dockerfile
```

În acelașo director de proiect creăm directorul site. În noul director creaăm fișierul index.html cu conținut arbitrar:

```bash
mkdir site
echo "<html><body><h1>Pagina mea!</h1></body></html>" > site/index.html
```

## Pornire și testare

Deschidem terminalul în directorul containers03 și executăm comanda:

```bash
docker build -t containers03 .
```

Ce a fost afișat în consolă?

![3](https://github.com/user-attachments/assets/7f9b3d20-c056-4168-9755-d0c09bd7e7b4)

Executăm comanda pentru a porni containerul:

```bash
docker run --name containers03 containers03
```

Ce a fost afișat în consolă?

![image](https://github.com/user-attachments/assets/5e58e241-4b44-497b-8b59-38b55d2458b5)

Ștergem containerul și pornițim din nou, executând comenzile:

```bash
docker rm containers03
docker run -ti --name containers03 containers03 bash
```

În fereastra deschisă, executăm comenzile:

```bash
cd /var/www/html/
ls -l
```

Ce este afișat pe ecran?

![image](https://github.com/user-attachments/assets/26deec58-d3be-4c97-9f40-c971e5eb7110)

Închideți fereastra cu comanda exit.

## Concluzie

Lucrarea de față ne oferă o oportunitate de a ne familiariza cu procesul de lucru cu containerele Docker, o tehnologie care revoluționează modul în care aplicațiile sunt dezvoltate și gestionate. Containerele Docker oferă o metodă convenabilă și eficientă de a dezvolta și rula aplicații într-un mediu izolat de sistemul gazdă, având integrată toate dependențele necesare, librăriile și aplicațiile externe. Acest lucru permite crearea unui mediu uniform de lucru, indiferent de sistemul pe care rulează aplicația, garantând astfel consistența în rulare. În plus, în caz de erori, containerele pot fi reinstalate rapid împreună cu aplicația, oferind o soluție rapidă și eficientă pentru rezolvarea problemelor și menținerea unui flux de lucru stabil.

## Bibliografie

[^1]: [Docker Desktop](https://www.docker.com/products/docker-desktop/)
[^2]: [Git](https://docs.github.com/ru/get-started/git-basics/set-up-git)
