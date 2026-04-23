# iPogo Installer

Instalador gráfico do iPogo para Linux — sideload no iPhone sem complicação.

---

## Instalação rápida

```bash
bash ~/Compartilhado/ipogo-sideload/instalar.sh
```

Após rodar, o **iPogo Installer** aparece no menu de aplicativos do GNOME.

---

## Requisitos

- Linux Ubuntu / Debian (x86_64)
- Docker instalado
- iPhone conectado via cabo USB
- Apple ID (com ou sem 2FA)

---

## Passo a passo para instalar o iPogo

1. **Conecte o iPhone** via cabo USB → desbloqueie → toque em **Confiar** se aparecer
2. **Selecione o IPA** — arraste na interface ou cole a URL e clique em Baixar
   - Baixe o `.ipa` em [ipogo.app](https://ipogo.app)
3. **Preencha o Apple ID** — email e senha
4. **2FA** (se ativado) — aguarde o código aparecer no iPhone e digite na janela que abre automaticamente
5. Clique em **Instalar iPogo** e aguarde — não desconecte o cabo
6. **No iPhone** — obrigatório após instalar:
   - Ajustes → Geral → VPN e Gerenciamento de Dispositivo → seu Apple ID → **Confiar**

---

## Atualizar o iPogo (nova versão do app)

Quando sair uma nova versão do iPogo:

1. Baixe o novo `.ipa` em [ipogo.app](https://ipogo.app)
2. Abra o iPogo Installer
3. Selecione o novo `.ipa` (arraste ou use a URL)
4. Clique em Instalar — sobrescreve a versão antiga automaticamente

---

## Atualizar o iPogo Installer (nova versão do instalador)

Para compilar e publicar uma nova versão do instalador:

```bash
bash ~/Compartilhado/ipogo-sideload/nova-versao.sh
```

O script:
- Pede a versão (ex: `1.1.0`)
- Pede uma descrição
- Compila o binário automaticamente
- Publica no GitHub Releases

---

## Comandos úteis

| Ação | Comando |
|------|---------|
| Abrir o instalador | `iPogo-Installer` |
| Ver iPhone conectado | `lsusb \| grep Apple` |
| Reiniciar Anisette | `docker restart anisette` |
| Ver log do Anisette | `docker logs anisette --tail 30` |
| Status dos containers | `docker ps` |
| UDID do iPhone | `idevice_id -l` |
| Reinstalar no PC | `bash ~/Compartilhado/ipogo-sideload/instalar.sh` |
| Nova versão do instalador | `bash ~/Compartilhado/ipogo-sideload/nova-versao.sh` |

---

## Problemas comuns

| Problema | Solução |
|----------|---------|
| iPhone não detectado | Troque o cabo → desbloqueie → toque em Confiar |
| Erro de autenticação | Verifique email/senha → gere senha de app em [appleid.apple.com](https://appleid.apple.com) |
| Anisette falhou | `docker restart anisette` → aguarde 10s → tente novamente |
| App trava ao abrir no iPhone | Fez o passo de Confiar no perfil? (veja passo 6 acima) |
| IPA inválido | Baixe novamente em [ipogo.app](https://ipogo.app) — arquivo corrompido |
| Timeout na instalação | iPhone bloqueou durante instalação — mantenha desbloqueado |
| Instalou mas mostra erro na interface | Verifique o log — se aparecer "successfully installed" foi sucesso |

---

## Estrutura dos arquivos

```
~/Compartilhado/ipogo-sideload/
├── iPogo-Installer       ← binário compilado
├── ipogo-gui.py          ← código-fonte da interface
├── instalar.sh           ← instala no sistema (menu de apps)
├── nova-versao.sh        ← compila e publica nova release
├── AltServer-Linux       ← binário do AltServer
├── icon.png              ← ícone do app
└── ipogo-X.X.X.ipa       ← arquivo IPA do iPogo
```

---

## Links

- [Página de download](https://vinicius-emanuel-costa.github.io/ipogo-installer/)
- [Releases](https://github.com/vinicius-emanuel-costa/ipogo-installer/releases)
- [iPogo oficial](https://ipogo.app)
