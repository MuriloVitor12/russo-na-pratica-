# russo-na-pratica-
site para aprender russo 
from pathlib import Path
import zipfile

source = Path("/mnt/data/russo_na_pratica_desafios.html")
site_dir = Path("/mnt/data/russo_na_pratica_publicar")
site_dir.mkdir(exist_ok=True)
(site_dir / "index.html").write_text(source.read_text(encoding="utf-8"), encoding="utf-8")
(site_dir / "LEIA-ME.txt").write_text(
"""RUSSO NA PRÁTICA — PUBLICAÇÃO GRATUITA

Este pacote contém o site em index.html.

Como publicar gratuitamente no GitHub Pages:
1. Entre em https://github.com/ e crie uma conta, se ainda não tiver.
2. Crie um repositório novo chamado russo-na-pratica.
3. Envie o arquivo index.html para esse repositório (Add file > Upload files > Commit changes).
4. Abra Settings > Pages.
5. Em Build and deployment, selecione Deploy from a branch.
6. Escolha a branch main e a pasta /(root), depois salve.
7. Aguarde a publicação. O GitHub mostrará o endereço público na página Settings > Pages.

Observação: eu preparei os arquivos, mas não publiquei o site. Para publicar no seu nome, é necessário entrar na sua conta de hospedagem e concluir os passos acima.
""", encoding="utf-8")
zip_path = Path("/mnt/data/russo_na_pratica_site_publico.zip")
with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as z:
    z.write(site_dir / "index.html", "index.html")
    z.write(site_dir / "LEIA-ME.txt", "LEIA-ME.txt")
print(f"Pacote criado: {zip_path} ({zip_path.stat().st_size:,} bytes)")
