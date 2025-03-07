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

![Instalare](1.png)

## Executare

Creăm un repozitoriu containers03:

![Repozitor](2.png)

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
