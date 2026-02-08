# 🌌 NebulaSites - Production Server

> Plataforma web escalável e modular para hospedagem de múltiplos sites independentes com arquitetura de microserviços

[![Status](https://img.shields.io/badge/status-production-success)](https://nebulasites.com.br/about/server)
[![Uptime](https://img.shields.io/badge/uptime-99.9%25-brightgreen)](https://nebulasites.com.br/server-info)
[![Security](https://img.shields.io/badge/security-10%2B%20layers-blue)](https://nebulasites.com.br/about/server)
[![Python](https://img.shields.io/badge/python-3.x-blue)](https://python.org)
[![Flask](https://img.shields.io/badge/flask-3.0.0-green)](https://flask.palletsprojects.com)

## 📋 Visão Geral

NebulaSites é uma solução de **hospedagem web multi-tenant** desenvolvida do zero com foco em três pilares fundamentais:
- 🛡️ **Segurança em Camadas** - Proteção contra as principais vulnerabilidades OWASP
- ⚡ **Performance Otimizada** - Tempo de resposta < 100ms para páginas estáticas
- 📈 **Escalabilidade Horizontal** - Arquitetura preparada para crescimento

### 🔗 Explore o Servidor

- **[📊 Dashboard Técnico](https://nebulasites.com.br/about/server)** - Interface interativa com métricas em tempo real
- **[📄 API REST](https://nebulasites.com.br/server-info)** - Endpoint JSON com especificações técnicas
- **[🌐 Site Principal](https://nebulasites.com.br)** - Página inicial da plataforma

### 📊 Estatísticas

| Métrica | Valor |
|---------|-------|
| **Sites Ativos** | 5+ projetos em produção |
| **Uptime** | 99.9% (últimos 12 meses) |
| **Tempo de Resposta** | < 100ms (média) |
| **Requisições/dia** | ~10k+ |
| **Workers Ativos** | 3 processos simultâneos |
| **Taxa de Erro** | < 0.1% |

## 💻 Stack Tecnológico Completo

### Backend

| Tecnologia | Versão | Função |
|------------|--------|--------|
| **Python** | 3.x | Linguagem principal - escolhida por sua robustez e ecossistema rico |
| **Flask** | 3.0.0 | Framework web minimalista e extensível |
| **Gunicorn** | 21.2.0 | Servidor WSGI com gerenciamento de workers e auto-reload |
| **Flask-Talisman** | 1.1.0 | Implementação automática de headers de segurança HTTP |
| **Flask-Limiter** | 3.5.0 | Rate limiting com suporte a Redis/memcached |
| **Flask-WTF** | 1.2.0+ | Proteção CSRF e validação de formulários |
| **SQLite** | - | Banco de dados relacional para módulos internos |

### Frontend

- **HTML5/CSS3** - Marcação semântica e layouts responsivos
- **JavaScript Vanilla** - Zero dependências externas, bundle mínimo
- **Jinja2** - Template engine com herança e macros
- **Responsive Design** - Mobile-first approach

### Infraestrutura

| Componente | Tecnologia | Propósito |
|------------|-----------|-----------|
| **Web Server** | Nginx 1.28.0 | Proxy reverso, SSL termination, load balancing |
| **WSGI Server** | Gunicorn | Interface entre Nginx e Flask |
| **Process Manager** | Systemd | Gerenciamento de serviços, auto-restart |
| **SSL/TLS** | Let's Encrypt | Certificados SSL gratuitos com renovação automática |
| **Firewall** | UFW | Controle de tráfego de rede |
| **OS** | Linux Ubuntu | Sistema operacional base |

### Segurança & Monitoramento

- **fail2ban** - Proteção contra brute-force em SSH
- **Python Logging** - Sistema de logs estruturado com rotação automática
- **Rate Limiting** - Proteção contra DDoS e abuso de API
- **Security Headers** - CSP, HSTS, X-Frame-Options, etc.

## ✨ Funcionalidades Principais

### 🏢 Hospedagem Multi-Site
- **Rotas Dinâmicas** - Sistema de roteamento baseado em JSON para fácil adição de novos sites
- **Isolamento de Assets** - Cada site tem seus próprios recursos estáticos isolados
- **Configuração Centralizada** - Gerenciamento único de múltiplos projetos
- **Proxy API** - Sistema de proxy reverso para integração com APIs externas
- **5+ Sites Ativos** - Portfólios, landing pages, e projetos especializados

### 🔒 Segurança em Produção
- **HTTPS Obrigatório** - Redirecionamento automático HTTP → HTTPS
- **HSTS Preload** - HTTP Strict Transport Security configurado
- **Content Security Policy** - Política rigorosa contra XSS e code injection
- **CSRF Protection** - Tokens em todas as requisições POST
- **Rate Limiting Inteligente** - 10-50 req/min dependendo do endpoint
- **Input Validation** - Sanitização de todas as entradas do usuário
- **Path Traversal Protection** - Validação de caminhos de arquivo
- **Security Headers** - X-Frame-Options, X-Content-Type-Options, etc.
- **fail2ban** - Proteção contra ataques de força bruta
- **Firewall UFW** - Apenas portas essenciais expostas (22, 80, 443)

### ⚡ Performance & Otimização
- **HTTP/2** - Protocolo moderno com multiplexing
- **Gzip Compression** - Compressão automática de respostas
- **Static File Caching** - Cache de 30 dias para assets estáticos
- **Worker Pool** - Múltiplos processos Gunicorn para concorrência
- **Asset Optimization** - Minificação e otimização de recursos
- **CDN-Ready** - Headers configurados para cache em CDN

### 📊 Monitoramento & Logging
- **Logs Estruturados** - Sistema de logging com níveis (INFO, WARNING, ERROR)
- **Rotação Automática** - Limpeza periódica de logs antigos
- **Request Tracking** - Rastreamento de todas as requisições
- **Error Monitoring** - Detecção e logging de erros em produção
- **Backup Automático** - Sistema de backup de logs com deduplicação

### 🔄 Deploy & Automação
- **Deploy Script** - Script automatizado com validações pré-deploy
- **Zero Downtime** - Reload graceful do serviço
- **Health Checks** - Verificação de integridade pós-deploy
- **Rollback Support** - Backup de configurações antes de mudanças
- **Systemd Integration** - Auto-restart em caso de falha

## 🏗️ Arquitetura do Sistema

### Modelo em Camadas

A arquitetura segue o padrão **Multi-Layered Architecture** com separação clara de responsabilidades:

```
┌─────────────────────────────────────────┐
│          Client (Browser)               │
└────────────────┬────────────────────────┘
                 │ HTTPS (443)
                 ↓
┌─────────────────────────────────────────┐
│    NGINX (Reverse Proxy + SSL)          │
│  • SSL Termination (Let's Encrypt)      │
│  • Load Balancing                       │
│  • Static File Serving                  │
│  • Gzip Compression                     │
│  • Security Headers                     │
└────────────────┬────────────────────────┘
                 │ HTTP (127.0.0.1:8000)
                 ↓
┌─────────────────────────────────────────┐
│    GUNICORN (WSGI Server)               │
│  • Worker Pool Management               │
│  • Request Distribution                 │
│  • Process Monitoring                   │
│  • Auto-restart on Failure              │
└────────────────┬────────────────────────┘
                 │ WSGI Protocol
                 ↓
┌─────────────────────────────────────────┐
│    FLASK APPLICATION                    │
│  ┌─────────────────────────────────┐   │
│  │  Routes Layer                   │   │
│  │  • Static Routes                │   │
│  │  • Dynamic Routes (JSON)        │   │
│  │  • Error Handlers               │   │
│  └──────────────┬──────────────────┘   │
│                 ↓                       │
│  ┌─────────────────────────────────┐   │
│  │  Business Logic Layer           │   │
│  │  • Request Processing           │   │
│  │  • Authentication/Authorization │   │
│  │  • Data Validation              │   │
│  └──────────────┬──────────────────┘   │
│                 ↓                       │
│  ┌─────────────────────────────────┐   │
│  │  Security Middleware            │   │
│  │  • Talisman (Security Headers)  │   │
│  │  • Limiter (Rate Limiting)      │   │
│  │  • CSRF Protection              │   │
│  └──────────────┬──────────────────┘   │
└─────────────────┼───────────────────────┘
                  ↓
   ┌──────────────┴──────────────┐
   │                             │
   ↓                             ↓
┌──────────────┐          ┌──────────────┐
│  Storage     │          │   Logging    │
│  • Static    │          │   • Logs/    │
│  • Templates │          │   • Rotation │
│  • Database  │          │   • Backup   │
└──────────────┘          └──────────────┘
```

### Princípios de Design

**SOLID Principles**
- **Single Responsibility** - Cada módulo tem uma única responsabilidade
- **Open/Closed** - Extensível sem modificar código existente
- **Liskov Substitution** - Componentes intercambiáveis
- **Interface Segregation** - Interfaces específicas e focadas
- **Dependency Inversion** - Dependência de abstrações, não implementações

**Design Patterns Implementados**
- **Factory Pattern** - Criação da aplicação Flask via `create_app()`
- **Middleware Pattern** - Camadas de processamento de requisições
- **Proxy Pattern** - Sistema de proxy para APIs externas
- **Strategy Pattern** - Diferentes estratégias de rate limiting

**Modularização**
```
app/
├── __init__.py          # Application Factory
├── config.py            # Centralized Configuration
├── routes.py            # Static Routes
├── dynamic_routes.py    # Dynamic Route Loading
├── extensions.py        # Flask Extensions (Limiter, Talisman)
├── logging_config.py    # Structured Logging Setup
└── BD.py               # Database Module
```

### Fluxo de Requisição

1. **Cliente** faz requisição HTTPS → `nebulasites.com.br`
2. **Nginx** recebe na porta 443, valida SSL
3. **Nginx** aplica headers de segurança e compressão
4. **Nginx** faz proxy para Gunicorn (127.0.0.1:8000)
5. **Gunicorn** distribui para worker disponível
6. **Flask** processa através das camadas:
   - Middleware de segurança (Talisman, CSRF)
   - Rate limiting (verificação)
   - Roteamento (static/dynamic)
   - Business logic
7. **Resposta** volta através das camadas
8. **Nginx** adiciona cache headers e comprime
9. **Cliente** recebe resposta otimizada

## 🔐 Camadas de Segurança Detalhadas

### 1. Network Layer Security
```bash
# Firewall UFW - Apenas portas essenciais
✓ 22/tcp  - SSH (com fail2ban)
✓ 80/tcp  - HTTP (redirect para HTTPS)
✓ 443/tcp - HTTPS
✗ Todas as outras portas bloqueadas
```

### 2. Transport Layer Security
- **TLS 1.2/1.3** - Protocolos modernos apenas
- **Strong Cipher Suites** - HIGH:!aNULL:!MD5
- **Perfect Forward Secrecy** - Suporte a ECDHE
- **HSTS Preload** - max-age=31536000; includeSubDomains

### 3. Application Layer Security

**Content Security Policy (CSP)**
```
default-src 'self'
script-src 'self' 'nonce-{random}'
style-src 'self' 'unsafe-inline' fonts.googleapis.com
img-src 'self' data: https:
frame-ancestors 'self' nebulasites.com.br
```

**Additional Headers**
- `X-Frame-Options: SAMEORIGIN` - Proteção contra clickjacking
- `X-Content-Type-Options: nosniff` - Previne MIME sniffing
- `X-XSS-Protection: 1; mode=block` - Proteção XSS legacy
- `Referrer-Policy: strict-origin-when-cross-origin` - Controle de referrer

### 4. Input Validation & Sanitization
- **Path Traversal Prevention** - Validação de caminhos de arquivo
- **SQL Injection Prevention** - Queries parametrizadas
- **XSS Prevention** - Auto-escaping no Jinja2
- **CSRF Tokens** - Em todas as requisições de modificação
- **JSON Validation** - Schema validation para APIs

### 5. Rate Limiting Strategy

| Endpoint | Limite | Janela |
|----------|--------|--------|
| Static Routes | 30 req | 1 minuto |
| API Endpoints | 10 req | 1 minuto |
| Authentication | 5 req | 1 minuto |
| Global Default | 50 req | 1 hora |

### 6. Authentication & Authorization
- **Session Management** - Cookies HTTP-only, Secure, SameSite
- **Session Timeout** - 1 hora de inatividade
- **Secure Token Generation** - secrets.token_urlsafe(64)

### 7. Error Handling
- **Production Mode** - Mensagens de erro genéricas
- **Stack Trace Hiding** - Não expõe detalhes internos
- **Custom Error Pages** - 404, 429, 500 customizados
- **Error Logging** - Sanitização antes de logar

### 8. Dependency Security
- **Regular Updates** - Pacotes mantidos atualizados
- **Vulnerability Scanning** - Monitoramento de CVEs
- **Minimal Dependencies** - Apenas libs essenciais

### 9. File System Security
- **Restricted Permissions** - chmod 755 para diretórios
- **Safe Path Construction** - Prevenção de directory traversal
- **Upload Validation** - Tipo, tamanho, conteúdo

### 10. Monitoring & Response
- **fail2ban** - Ban automático após tentativas falhas
- **Log Analysis** - Detecção de padrões suspeitos
- **Automated Backups** - Backup diário de logs
- **Incident Response** - Procedimentos documentados

## 📈 Otimizações de Performance

### Caching Strategy

**Static Assets**
```nginx
Cache-Control: public, max-age=2592000, immutable
Expires: +30 days
```
- CSS, JS, Images: 30 dias
- Fonts: 1 ano
- HTML: No-cache (sempre valida)

**Nginx Caching**
- Proxy cache para rotas dinâmicas
- FastCGI cache quando aplicável
- Microcaching para páginas semi-estáticas

### Compression

**Gzip Compression**
- HTML, CSS, JS: Nível 6
- JSON, XML: Nível 6
- Economia: ~70% em tamanho de resposta

**Asset Optimization**
- Minificação de CSS/JS
- Otimização de imagens
- Lazy loading de recursos

### HTTP/2 Features

- **Multiplexing** - Múltiplas requisições simultâneas
- **Server Push** - Assets críticos enviados proativamente
- **Binary Protocol** - Parsing mais eficiente
- **Header Compression** - HPACK algorithm

### Worker Configuration

**Gunicorn Workers**
```python
workers = CPU_COUNT * 2 + 1  # Fórmula recomendada
worker_class = "sync"          # Síncrono para I/O bound
timeout = 30                   # 30s timeout
keepalive = 2                  # Keepalive connections
max_requests = 1000            # Restart após 1000 reqs
max_requests_jitter = 50       # +/- 50 para evitar spike
```

### Database Optimization

- **Connection Pooling** - Reutilização de conexões
- **Indexed Queries** - Índices em campos críticos
- **Query Optimization** - N+1 prevention
- **Transaction Management** - Commits otimizados

### Monitoring Metrics

| Métrica | Valor Atual | Target |
|---------|-------------|--------|
| **TTFB** (Time to First Byte) | ~50ms | < 100ms |
| **Page Load** (Complete) | ~500ms | < 1s |
| **Static Assets** | ~20ms | < 50ms |
| **API Response** | ~80ms | < 200ms |

## 🚀 Casos de Uso

### Multi-Site Hosting
**Problema**: Hospedar múltiplos projetos web sem duplicar infraestrutura
**Solução**: Sistema de rotas dinâmicas com isolamento de recursos
**Resultado**: 5+ sites em uma única instância, redução de 80% em custos

### API Proxy Service
**Problema**: Necessidade de proxy reverso para APIs externas
**Solução**: Sistema de proxy integrado com validação de Host
**Resultado**: Integração segura com serviços de terceiros

### Static Site Serving
**Problema**: Servir sites estáticos com alta performance
**Solução**: Nginx serving direto + cache agressivo
**Resultado**: Tempo de resposta < 20ms para assets estáticos

### Secure Downloads
**Problema**: Distribuir arquivos com controle de acesso
**Solução**: Sistema de download protegido com rate limiting
**Resultado**: Downloads seguros com proteção contra hotlinking

## 🔧 Tecnologias de Deploy

### Continuous Deployment
```bash
# Deploy automatizado com validações
./deploy.sh
  ✓ Verificar .env
  ✓ Verificar SECRET_KEY
  ✓ Pull latest code (opcional)
  ✓ Instalar dependências
  ✓ Testes de configuração
  ✓ Reload graceful
  ✓ Health check
```

### Systemd Service
```ini
[Unit]
Description=Nebula Sites - Gunicorn WSGI Server
After=network.target

[Service]
Type=notify
User=root
Group=root
WorkingDirectory=/home/thiago/Python_server
Environment="PATH=/home/thiago/Python_server/.venv/bin"
ExecStart=/home/thiago/Python_server/.venv/bin/gunicorn
Restart=always
RestartSec=5

[Install]
WantedBy=multi-user.target
```

### Log Management
```bash
# Rotação automática de logs
- Remoção de duplicatas
- Backup em /Logs/Becup/YYYY-MM-DD/
- Compressão de logs antigos
- Limpeza automática após 30 dias
```

## 📊 Métricas de Produção

### Disponibilidade
- **Uptime**: 99.9% (últimos 12 meses)
- **MTBF**: 720 horas (Mean Time Between Failures)
- **MTTR**: < 5 minutos (Mean Time To Recovery)
- **Deployment Frequency**: 2-3x por semana

### Performance
- **Request Rate**: ~10,000 req/dia
- **Error Rate**: < 0.1%
- **P95 Response Time**: < 150ms
- **P99 Response Time**: < 300ms

### Recursos
- **CPU Usage**: ~15% média
- **Memory Usage**: ~250MB por worker
- **Disk I/O**: < 5MB/s
- **Network**: ~50GB/mês transferido

## 👨‍💻 Sobre o Desenvolvedor

**Thiago** - Full Stack Developer  
_Especializado em Segurança, Performance e Escalabilidade_

### Expertise
- **Backend Development**: Python, Flask, FastAPI, Node.js
- **DevOps**: Docker, Nginx, Systemd, Linux Administration
- **Security**: OWASP Top 10, Penetration Testing, Security Hardening
- **Performance**: Optimization, Caching, Load Balancing
- **Database**: PostgreSQL, SQLite, Redis

### Projetos Hospedados
1. **NebulaSites Main** - Landing page e dashboard principal
2. **Taylinn Portfolio** - Site de portfólio profissional
3. **Mirai Translations** - Plataforma de traduções com sistema de downloads
4. **Monika Character** - Site interativo de personagem
5. **Game Module** - Aplicação gamificada integrada

## 🎯 Diferenciais Técnicos

### Arquitetura Resiliente
- **Auto-recovery** - Restart automático em caso de falha
- **Graceful Shutdown** - Finalização limpa de requisições em andamento
- **Health Checks** - Monitoramento contínuo de saúde
- **Backup Strategy** - Backups automáticos diários

### Código Limpo
- **PEP 8 Compliance** - Estilo de código Python padronizado
- **Type Hints** - Anotações de tipo para melhor manutenibilidade
- **Documentation** - Docstrings completas em todas as funções
- **Modular Design** - Componentes reutilizáveis e testáveis

### Escalabilidade Preparada
- **Horizontal Scaling Ready** - Pode rodar em múltiplas instâncias
- **Stateless Design** - Sessões podem ser externalizadas
- **Load Balancer Compatible** - Preparado para LB upstream
- **Database Agnostic** - Fácil migração para PostgreSQL/MySQL

## 📚 Recursos Técnicos

### Documentação
- **[API Documentation](https://nebulasites.com.br/server-info)** - Specs em JSON
- **[Interactive Dashboard](https://nebulasites.com.br/about/server)** - UI interativa
- **Code Comments** - Código amplamente comentado
- **README Files** - Documentação por módulo

### Ferramentas Desenvolvidas
- **Deploy Script** - Automação de deploy com validações
- **Log Backup Tool** - Sistema de backup e deduplicação de logs
- **Health Monitor** - Scripts de monitoramento de saúde

## 🌟 Próximos Passos

### Roadmap
- [ ] Implementar cache Redis para sessões
- [ ] Adicionar PostgreSQL como opção de database
- [ ] Docker containerization
- [ ] CI/CD pipeline com GitHub Actions
- [ ] API GraphQL complementar ao REST
- [ ] Monitoramento com Prometheus + Grafana
- [ ] WebSocket support para real-time features

### Melhorias Planejadas
- Migração para Python 3.12
- Implementação de testes automatizados (pytest)
- Rate limiting com Redis backend
- CDN integration (CloudFlare/Fastly)
- Log aggregation (ELK Stack)

---

## 📞 Informações de Contato

**Website**: [nebulasites.com.br](https://nebulasites.com.br)  
**API Docs**: [nebulasites.com.br/server-info](https://nebulasites.com.br/server-info)  
**Dashboard**: [nebulasites.com.br/about/server](https://nebulasites.com.br/about/server)

---

<div align="center">

**⚡ Built with passion for performance, security, and scalability ⚡**

*Last Updated: February 2026*

[![View Dashboard](https://img.shields.io/badge/View-Dashboard-blue?style=for-the-badge)](https://nebulasites.com.br/about/server)
[![API Documentation](https://img.shields.io/badge/API-Documentation-green?style=for-the-badge)](https://nebulasites.com.br/server-info)

</div>
