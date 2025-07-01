# MinerCloud BTC – Módulo de Afiliados

Este é o módulo completo de sistema de afiliados para o app **MinerCloud BTC**, desenvolvido em Flutter + Firebase.

## 🚀 Funcionalidades

✅ Geração de link único por usuário (com código de afiliado)  
✅ Comissão de 5% dos ganhos de mineração dos indicados  
✅ Painel de afiliados com total de indicados e ganhos  
✅ QR Code para compartilhamento do link de convite  
✅ Sistema antifraude com Firebase Auth e controle de IP (sugestão via Cloud Functions)

---

## 🧱 Estrutura do Projeto

```
affiliate_module/
├── lib/
│   ├── auth_service.dart             # Criação do perfil com código de afiliado
│   ├── signup_screen.dart            # Salvamento do código de quem indicou
│   ├── affiliate_commission.dart     # Lógica para calcular comissão (5%)
│   └── affiliate_dashboard.dart      # Tela com painel de afiliados + QR Code
├── pubspec.yaml                      # Dependências necessárias
├── README.md                         # Este arquivo
```

---

## 📦 Dependências

```yaml
dependencies:
  flutter:
    sdk: flutter
  firebase_auth: ^4.2.5
  cloud_firestore: ^4.0.3
  qr_flutter: ^4.0.0
```

---

## 🔗 Exemplo de link de convite

Links de convite devem ser gerados com [Firebase Dynamic Links](https://firebase.google.com/docs/dynamic-links):

```
https://minercloud.page.link/?ref=UZIabc123
```

---

## 👨‍💻 Integração no App

1. Importe os arquivos `.dart` em seu projeto principal
2. No cadastro de usuário, use `createUserProfile(user)` após o login.
3. Se o campo "indicação" for preenchido, use `saveReferralIfExists(...)`
4. Após mineração, chame `updateAffiliateCommission(...)`
5. Adicione a tela `AffiliateDashboard()` onde quiser mostrar o painel

---

## 🔒 Segurança recomendada

- Usar Firebase Auth para evitar múltiplas contas fake
- Criar Firebase Functions para validar IP único por indicação
- Bloquear autoindicação (verificar se `uid == referredBy`)

---

## 🧠 Autor

Criado por [UziMdeus](https://github.com/UziMdeus) para o projeto [MinerCloud BTC](https://minercloudbtc.com)
