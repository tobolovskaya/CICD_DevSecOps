# 🛡️ Домашнє завдання: Аналіз безпекових ризиків у процесі контролю змін

## 📋 Зв'язок з лабораторною роботою

Це завдання є **логічним продовженням** лабораторної роботи "Аудит змін у репозиторії GitLab".

```
┌─────────────────────────────────────────────────────────────────┐
│  ЛАБОРАТОРНА РОБОТА (виконано)                                  │
│  ↓                                                               │
│  ✅ Технічне розслідування:                                     │
│  • Знайдено проблемний коміт                                    │
│  • Проаналізовано зміни в test_app.py                           │
│  • Виявлено порушення політик (no review, no signature)        │
│  • Зафіксовано технічні факти                                   │
│  • Оцінено відповідність SCM політикам                          │
└─────────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────────┐
│  ДОМАШНЄ ЗАВДАННЯ (виконується зараз)                           │
│  ↓                                                               │
│  🎯 Стратегічне планування:                                     │
│  • Моделювання реальних інцидентів                              │
│  • Розробка превентивних заходів                                │
│  • Технічні та організаційні рішення                            │
│  • Формування культури безпеки в команді                        │
│  • Комплексний план покращення процесів                         │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🎯 Мета роботи

Навчитись:
- Виявляти та пояснювати безпекові ризики в процесі контролю змін
- Моделювати реалістичні сценарії інцидентів
- Розробляти превентивні технічні та організаційні заходи
- Формувати культуру відповідальності без звинувачень
- Створювати комплексні стратегії покращення безпеки

---

## 📚 Вихідні умови

✅ Виконана лабораторна робота з аудиту Git змін  
✅ Зібрані технічні факти про зміну в test_app.py  
✅ Виявлені порушення політик (no review, no signature, direct push)  
✅ Результати CI/CD пайплайну (SAST FAIL)  
✅ Знання принципів SSDLC, SCM, аудиту змін

---

## 📝 Структура звіту (8 розділів)

**Обсяг:** 2-3 сторінки (без скриншотів та додатків)

### 1. Вступ
- Короткий опис кейсу
- Контекст інциденту
- Масштаб проблеми
- Цілі звіту

### 2. Технічний аналіз зміни
- Опис зміни (що, хто, коли)
- Змінені файли та рядки
- Виявлені вразливості
- Результати CI/CD

### 3. Перевірка автентичності
- Результати перевірки GPG/SSH підпису
- Ризики непідписаних комітів
- Аналіз non-repudiation

### 4. Оцінка відповідності політикам SCM
- Перелік порушених політик
- Детальний аналіз кожного порушення
- Чому створює ризик
- Зв'язок з SSDLC принципами

### 5. Моделювання інциденту
- Реалістичний сценарій безпекового інциденту
- Timeline атаки
- Як зміна потрапила в production
- Чому не була виявлена
- Наслідки для користувачів, бізнесу, команди

### 6. Превентивна стратегія
- Технічні заходи
- Організаційні заходи
- Автоматизація
- План впровадження

### 7. Формування культури
- Звернення до команди (до 200 слів)
- Конструктивний тон, без звинувачень
- Акцент на спільну мету

### 8. Висновки
- Важливість аудиту в SSDLC
- Підсумок рекомендацій
- Довгострокова стратегія

---

## 📖 Шаблони та приклади

### Шаблон розділу 1: Вступ

```markdown
# 1. ВСТУП

## 1.1 Контекст інциденту

[Дата] в репозиторії [назва проєкту] було виявлено критичну зміну 
в файлі test_app.py (коміт [SHA]), яка:
- Додала множинні критичні вразливості
- Призвела до збою CI/CD на етапі SAST
- Була внесена з порушенням усіх політик безпеки

Деталі коміту:
- Автор: [ім'я та email]
- Дата: [дата та час]
- Повідомлення: [текст]
- Гілка: main (прямий коміт)
- Підпис: відсутній
- Code review: не проводився

## 1.2 Масштаб проблеми

Цей інцидент виявив системні недоліки:

**Технічні:**
- Branch protection rules не налаштовані
- Відсутня обов'язкова валідація перед merge
- CI/CD спрацьовує після потрапляння в main
- [інші проблеми з лабораторної]

**Процесні:**
- Code review не обов'язковий
- Відсутні чіткі політики SCM
- Культура "швидше = краще"

**Організаційні:**
- Недостатня автоматизація
- Відсутність відповідальності
- Немає метрик безпеки

## 1.3 Цілі звіту

1. Детальний аналіз порушень
2. Оцінка потенційних ризиків
3. Розробка превентивних заходів
4. Формування культури безпеки
5. План конкретних дій
```

---

### Шаблон розділу 2-4: Технічний аналіз

**Використайте дані з лабораторної роботи:**

```markdown
# 2. ТЕХНІЧНИЙ АНАЛІЗ ЗМІНИ

## 2.1 Ідентифікація коміту

| Параметр | Значення |
|----------|----------|
| Commit SHA | `[ваш SHA]` |
| Автор | `[ім'я та email з лабораторної]` |
| Дата | `[дата та час]` |
| Повідомлення | `[текст коміту]` |
| Гілка | `main` |
| Файли | `1 (test_app.py)` |
| Зміни | `+150, -80 рядків` |

## 2.2 Категоризація вразливостей

### Критичні (High Severity):

1. **Command Injection (CWE-78)**
   - Рядок: [номер з diff]
   - Код: `subprocess.call(command, shell=True)`
   - CVSS: 9.8
   - SAST: B602

2. **Code Execution (CWE-95)**
   - Рядки: [номери]
   - Код: `eval()`, `exec()`
   - CVSS: 9.8
   - SAST: B307, B102

3. **Hardcoded Secrets**
   - Рядки: [номери]
   - Типи: API keys, passwords
   - SAST: B105, B106

[Додайте всі вразливості з вашої лабораторної]

## 2.3 Результати CI/CD

Pipeline #[номер] результати:
- secret-scan: ⚠️ 3 secrets
- sast: ❌ FAILED (10+ High)
- test: не запущено
- build: не запущено

---

# 3. ПЕРЕВІРКА АВТЕНТИЧНОСТІ

## 3.1 Статус підпису

**Результат:** ❌ Коміт не підписаний

```bash
$ git verify-commit [SHA]
error: no signature found
```

## 3.2 Ризики

**Ризик 1: Неможливість верифікації автора**
- Git дозволяє підробити email
- Немає доказу справжності
- Можлива компрометація акаунта

**Ризик 2: Відсутність non-repudiation**
- Автор може заперечити авторство
- Юридичні складнощі
- Неможливо встановити відповідальність

**Ризик 3: Supply Chain Attack**
- Backdoor коміти без виявлення
- Компрометація developer machine
- Injection зловмисного коду

---

# 4. ОЦІНКА ВІДПОВІДНОСТІ ПОЛІТИКАМ SCM

## 4.1 Огляд порушень

| # | Політика | Статус | Severity |
|---|----------|--------|----------|
| 1 | Цифрові підписи | ❌ FAIL | CRITICAL |
| 2 | Code Review | ❌ FAIL | CRITICAL |
| 3 | Branch Protection | ❌ FAIL | HIGH |
| 4 | Pre-merge CI checks | ⚠️ WARN | HIGH |
| 5 | Документація змін | ❌ FAIL | MEDIUM |

## 4.2 Детальний аналіз

### ПОРУШЕННЯ #1: Відсутність підписів

**Політика:** Всі коміти в main ПОВИННІ бути підписані

**Чому створює ризик:**
- [пояснення з лабораторної]
- [можливі сценарії атак]
- [наслідки]

**Як порушує SSDLC:**
- Порушує принцип "Trust but Verify"
- Відсутність integrity control
- [інші зв'язки]

### ПОРУШЕННЯ #2: Відсутність Code Review

**Політика:** Всі зміни ПОВИННІ пройти peer review

**Чому створює ризик:**
- Пропуск вразливостей (reviewer побачив би eval/exec)
- Відсутність "security gate"
- Human error amplification

**Як порушує SSDLC:**
- Пропущена фаза Secure Code Review
- Defense in Depth відсутній
- [інші проблеми]

[Продовжте для всіх 5 порушень з вашої лабораторної]

## 4.3 Кумулятивний ефект

**"Swiss Cheese" модель:**
```
Layer 1 (Signing) → HOLE ❌
Layer 2 (Branch Protection) → HOLE ❌
Layer 3 (Code Review) → HOLE ❌
Layer 4 (CI Gates) → HOLE ❌
Result: Vulnerability проходить через всі layers
```

## 4.4 SSDLC відповідність

**Порушені фази:**
- Development: secure coding не дотримано
- Testing: security testing пізно
- Deployment: код в main без перевірок

**OWASP SAMM рівень:** Level 0-1 (Incomplete)
```

---

### Шаблон розділу 5: Моделювання інциденту

**Створіть реалістичний сценарій:**

```markdown
# 5. МОДЕЛЮВАННЯ ІНЦИДЕНТУ

## 5.1 Сценарій: [Назва, наприклад "Production Data Breach"]

### Контекст

**Компанія:** [Тип бізнесу, наприклад FinTech стартап]
**Користувачів:** [Кількість]
**Дані:** [Які дані обробляються]
**Compliance:** [GDPR, PCI DSS, тощо]
**Інфраструктура:** [AWS, Azure, on-prem]

### Timeline атаки

```
ДЕНЬ 1: [Дата коміту]
───────────────────────────────────────
14:32 - Коміт з вразливостями в main
14:33 - CI/CD fails (але код вже в main)
14:45 - Інші розробники pull вразливий код
15:30 - Merge через MR (вразливість залишається)
16:00 - Deploy в production

ДЕНЬ 5: [Через 4 дні]
───────────────────────────────────────
03:15 - 🚨 АТАКА РОЗПОЧАТА

Attacker discovery:
1. Сканує GitHub для публічних вразливостей
2. Знаходить eval() в test_app.py
3. Перевіряє production: https://api.company.com/test
4. Endpoints доступні ❌

03:20 - Initial exploitation

POST /test/execute
{
  "code": "__import__('os').system('whoami')"
}
→ RCE confirmed ✅

03:25 - Reconnaissance
- Витік AWS credentials з env
- Database connection strings
- Internal network mapping

03:45 - Data exfiltration
- Customer database: 50K users
- S3 documents: 200 GB
- Payment logs

04:30 - Backdoor installation
- SSH keys додано
- Admin user створено
- Crypto miner deployed

ДЕНЬ 6: [Наступний день]
───────────────────────────────────────
09:15 - 🔔 Detection: Abnormal AWS costs
10:15 - 🚨 INCIDENT DECLARED
10:20 - Incident Response activated

ДЕНЬ 7-14: Post-incident
───────────────────────────────────────
- Forensics: Root cause = коміт від [дата]
- Data exfiltrated: 215 GB
- Users affected: 50,000
```

## 5.2 Як зміна потрапила в production

**Root Cause Analysis (5 Whys):**

1. WHY вразливість в production?
   → Бо deploy з вразливим кодом

2. WHY код вразливий?
   → Бо eval() не виявлено

3. WHY не виявлено?
   → Бо без code review

4. WHY без review?
   → Бо direct push можливий

5. WHY direct push можливий?
   → Бо branch protection не налаштовано

**ROOT CAUSE:** Відсутність security gates

## 5.3 Чому не була виявлена

**Defense Layers (всі failed):**

```
Layer 1: Pre-commit checks → ❌ NOT IMPLEMENTED
Layer 2: Commit signing → ❌ NOT ENFORCED
Layer 3: Branch protection → ❌ WEAK
Layer 4: Code review → ❌ NOT REQUIRED
Layer 5: SAST pre-merge → ❌ RUNS AFTER
Layer 6: Security review → ❌ SKIPPED
Layer 7: DAST → ⚠️ PERIODIC ONLY
Result: 🚨 PRODUCTION BREACH
```

## 5.4 Наслідки

### Для користувачів:
- 50,000 users affected
- PII compromised (names, emails, addresses)
- Financial data exposed
- Identity theft risk
- Loss of trust

### Для бізнесу:
```
Фінансові втрати:
├─ Direct costs: $3.4M
│  ├─ Incident response: $150K
│  ├─ Forensics: $200K
│  ├─ Legal: $300K
│  ├─ Credit monitoring: $1.5M
│  └─ Remediation: $400K
│
├─ Indirect costs: $7-12M
│  ├─ Lost revenue (churn): $2M
│  ├─ Reputation damage: $5M
│  └─ Regulatory fines: $1-5M
│
└─ TOTAL: $10-15 MILLION
```

Operational:
- 2-3 weeks reduced capacity
- Payment processing suspended
- New signups halted
- Partnership delays

Regulatory:
- GDPR violations (Article 32, 33)
- PCI DSS non-compliance
- Regulatory investigations
- Possible business suspension

### Для команди:
- Intense pressure and scrutiny
- Potential terminations
- Psychological impact
- Team morale drop
- Increased turnover
- Hiring difficulties

## 5.5 Lessons Learned

1. Single point of failure = breach
2. CI/CD is critical infrastructure
3. Test code is real code
4. Culture > Process > Tools
5. Speed AND security are possible

**Висновок:** Multiple failures → "Swiss cheese" → breach
```

---

### Шаблон розділу 6: Превентивна стратегія

```markdown
# 6. ПРЕВЕНТИВНА СТРАТЕГІЯ

## 6.1 Технічні заходи

### 6.1.1 Git та GitLab конфігурація

**Пріоритет P0 (Негайно, < 1 день):**

**1. Branch Protection Rules**
```yaml
Protected Branch: main
├─ Allowed to push: No one ✅ (замість Maintainers)
├─ Allowed to merge: Maintainers only ✅
├─ Force push: Blocked ✅
├─ Require merge request: YES ✅
├─ Required approvals: 2 minimum ✅
├─ Dismiss stale approvals: YES ✅
├─ Require passing pipeline: YES ✅
├─ Require signed commits: YES ✅
└─ Code owner approval: YES ✅
```

**Як налаштувати:**
1. GitLab → Settings → Repository → Protected branches
2. Unprotect current main
3. Add protection з новими правилами
4. Test: спробувати direct push (має failed)

**2. Mandatory GPG Signatures**
```yaml
Requirement: All commits must be GPG signed

Implementation:
1. Generate GPG key:
   gpg --full-generate-key

2. Add to GitLab:
   Settings → GPG Keys → Add key

3. Configure Git:
   git config --global user.signingkey [KEY_ID]
   git config --global commit.gpgsign true

4. GitLab enforce:
   Settings → Push Rules → Reject unsigned commits
```

**3. Merge Request Template**
```markdown
## Description
[What changed and why]

## Security Checklist
- [ ] No hardcoded secrets
- [ ] No eval/exec usage
- [ ] Input validation present
- [ ] SQL queries parameterized
- [ ] Dependencies updated
- [ ] SAST passed
- [ ] Security team review (if needed)

## Testing
- [ ] Unit tests added/updated
- [ ] Integration tests passed
- [ ] Manual testing performed

## Related Issues
Closes #[issue number]
```

---

**Пріоритет P1 (Терміново, < 1 тиждень):**

**4. Pre-merge CI/CD Pipeline**
```yaml
# .gitlab-ci.yml
workflow:
  rules:
    - if: '$CI_PIPELINE_SOURCE == "merge_request_event"'

stages:
  - security
  - test
  - build

# Security Gate (blocking)
security-gate:
  stage: security
  script:
    # Secret scanning
    - detect-secrets scan --all-files
    
    # SAST
    - bandit -r . -f json -o bandit.json
    - bandit -r . -ll --exit-zero-on-error false
    
    # Dependency check
    - safety check --json
    
  allow_failure: false  # BLOCK if fails
  artifacts:
    reports:
      sast: bandit.json

# Require this job passes before merge allowed
```

**GitLab MR Settings:**
```
Settings → Merge Requests:
├─ Pipelines must succeed: YES ✅
├─ All discussions resolved: YES ✅
├─ Merge commit with semi-linear history: YES ✅
└─ Delete source branch after merge: YES ✅
```

**5. CODEOWNERS файл**
```
# .gitlab/CODEOWNERS

# Security-critical files require security team review
**/*test*.py @security-team
**/auth/** @security-team
**/api/** @backend-leads @security-team
**/*.env* @security-team
**/Dockerfile @devops-team @security-team
.gitlab-ci.yml @devops-team

# Default owners
* @tech-lead
```

---

**Пріоритет P2 (Важливо, < 1 місяць):**

**6. Pre-commit Hooks**
```bash
# .pre-commit-config.yaml
repos:
  - repo: https://github.com/Yelp/detect-secrets
    rev: v1.4.0
    hooks:
      - id: detect-secrets
        args: ['--baseline', '.secrets.baseline']
  
  - repo: https://github.com/PyCQA/bandit
    rev: 1.7.5
    hooks:
      - id: bandit
        args: ['-ll', '--skip', 'B101']
  
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.4.0
    hooks:
      - id: check-added-large-files
      - id: check-merge-conflict
      - id: check-yaml
      - id: end-of-file-fixer
```

**Встановлення для команди:**
```bash
pip install pre-commit
pre-commit install
pre-commit install --hook-type commit-msg
```

**7. Automated Security Scanning**
```yaml
# Daily scheduled security scan
scheduled-security-scan:
  stage: security
  script:
    - trivy filesystem .
    - snyk test
    - npm audit
  only:
    - schedules
  schedule: "0 2 * * *"  # 2 AM daily
```

---

### 6.1.2 CI/CD покращення

**8. Multi-stage Security Pipeline**
```
┌─────────────────────────────────────────────────────────────┐
│ MERGE REQUEST PIPELINE                                      │
├─────────────────────────────────────────────────────────────┤
│ Stage 1: Pre-checks (must pass)                            │
│  ├─ Lint and format check                                  │
│  ├─ Unit tests                                             │
│  └─ Secret scanning                                        │
│                                                             │
│ Stage 2: Security (must pass)                              │
│  ├─ SAST (Bandit, Semgrep)                                │
│  ├─ SCA (Safety, Snyk)                                     │
│  ├─ Container scanning (Trivy)                             │
│  └─ IaC scanning (Checkov)                                 │
│                                                             │
│ Stage 3: Build & Test (must pass)                          │
│  ├─ Build Docker image                                     │
│  ├─ Integration tests                                      │
│  └─ E2E tests                                              │
│                                                             │
│ Stage 4: Security validation (optional but report)         │
│  ├─ DAST (OWASP ZAP)                                       │
│  ├─ Dependency track                                       │
│  └─ License compliance                                     │
│                                                             │
│ → All stages pass → Merge Request can be approved         │
└─────────────────────────────────────────────────────────────┘
```

**9. Security Thresholds Policy**
```yaml
# Security policy configuration
security_policy:
  block_on:
    - cvss_score: >= 7.0  # High or Critical
    - secrets_found: > 0
    - license_violation: true
  
  warn_on:
    - cvss_score: >= 4.0  # Medium
    - outdated_dependencies: > 5
    - code_smell: > 10
  
  allow_with_approval:
    - cvss_score: < 4.0  # Low
    - false_positive_marked: true
```

---

### 6.1.3 Моніторинг та алерти

**10. Security Metrics Dashboard**
```yaml
Metrics to track:
├─ % MRs with security issues found
├─ Average time to fix Critical/High vulnerabilities
├─ Number of direct pushes attempted (should be 0)
├─ % commits with GPG signatures
├─ Security test coverage
└─ Mean time to detect (MTTD) security issues

Tools:
- GitLab Security Dashboard
- Grafana dashboards
- Custom scripts for metrics
```

**11. Alerting Setup**
```yaml
Alerts:
Critical (immediate notification):
  - Direct push attempt to main
  - Critical CVE in dependencies
  - Secrets committed
  - Production deployment failed
  Channels: PagerDuty, Slack, Email

High (within 4 hours):
  - High severity vulnerability
  - Security pipeline failure
  - Unsigned commit attempt
  Channels: Slack, Email

Medium (within 24 hours):
  - Medium severity issues
  - Outdated dependencies
  Channels: Slack, Weekly digest
```

---

## 6.2 Організаційні заходи

### 6.2.1 Політики та процедури

**12. Secure Development Policy**
```markdown
SECURITY DEVELOPMENT POLICY v1.0

1. CODE CHANGES
   All code changes MUST:
   - Go through Merge Request process
   - Have minimum 2 approvals
   - Pass all security checks
   - Be GPG signed
   - Have corresponding tests

2. SECURITY-CRITICAL CHANGES
   Changes to authentication, authorization, crypto, data handling:
   - Require Security Team review
   - Need threat modeling (if architectural)
   - Additional testing required

3. EMERGENCY PROCEDURES
   Even for hotfixes:
   - Create emergency MR
   - Get approval from on-call lead
   - Security team notified within 1 hour
   - Post-mortem within 24 hours

4. VIOLATIONS
   - First offense: Warning + training
   - Second offense: Written warning
   - Third offense: Performance review

5. RESPONSIBLE DISCLOSURE
   If you find vulnerability:
   - Report to security@company.com
   - Do NOT commit fix directly
   - Security team will coordinate
```

**13. Code Review Standards**
```markdown
SECURITY-FOCUSED CODE REVIEW CHECKLIST

For ALL reviews, check:
├─ [ ] No hardcoded secrets/credentials
├─ [ ] Input validation present
├─ [ ] Output encoding correct
├─ [ ] No SQL injection risks
├─ [ ] No command injection risks
├─ [ ] Error handling doesn't leak info
├─ [ ] Logging doesn't contain sensitive data
├─ [ ] Dependencies are up-to-date
└─ [ ] Tests cover security scenarios

For authentication/authorization changes:
├─ [ ] Principle of least privilege
├─ [ ] No broken access control
├─ [ ] Session management secure
└─ [ ] MFA considered

For data handling:
├─ [ ] Sensitive data encrypted
├─ [ ] PII handling compliant (GDPR)
└─ [ ] Data retention policies followed

Red flags to reject immediately:
├─ 🚩 eval(), exec() usage
├─ 🚩 shell=True in subprocess
├─ 🚩 pickle.loads() of untrusted data
├─ 🚩 Hardcoded passwords/keys
└─ 🚩 Disabled security features
```

---

### 6.2.2 Навчання та культура

**14. Security Training Program**
```
MANDATORY TRAINING:

Week 1 (Onboarding):
├─ Security basics and company policies
├─ Git signing setup
├─ Secure coding principles
└─ How to use security tools

Monthly:
├─ Security brown bags (1 hour)
├─ Vulnerability reviews (what happened, lessons)
└─ New threats and mitigations

Quarterly:
├─ OWASP Top 10 deep dive
├─ Secure code review workshop
└─ Threat modeling session

Annually:
├─ Security certification (OWASP, SANS, etc.)
├─ Red team exercises
└─ Security champions program
```

**15. Security Champions Program**
```markdown
SECURITY CHAMPIONS INITIATIVE

Goal: Embed security expertise in every team

Structure:
- 1 Security Champion per team (5-7 people)
- Champions get extra training
- 20% time for security activities
- Direct line to Security Team

Responsibilities:
1. Review security-critical MRs in their team
2. Share security updates in team meetings
3. Conduct security design reviews
4. Help teammates with security questions
5. Report potential issues to Security Team

Benefits:
- Priority access to training
- Security certification sponsorship
- Recognition in performance reviews
- Networking with other champions
```

**16. Gamification & Incentives**
```
SECURITY REWARDS PROGRAM

Points for:
├─ Finding vulnerability before production: 100 pts
├─ Security-focused MR: 10 pts
├─ Attending security training: 20 pts
├─ Writing security documentation: 30 pts
├─ Helping teammate with security: 15 pts
└─ 100% GPG signed commits (month): 50 pts

Rewards:
├─ 500 pts: Security book of choice
├─ 1000 pts: Security conference ticket
├─ 2000 pts: Bug bounty split
└─ 5000 pts: Bonus + Security Champion title

Leaderboard:
- Monthly team standings
- Individual recognition
- Not punitive, purely positive
```

---

### 6.2.3 Incident Response

**17. Security Incident Response Plan**
```markdown
INCIDENT RESPONSE PLAYBOOK

Phase 1: Detection (0-30 min)
├─ Alert received (automated or manual)
├─ On-call security engineer assigned
├─ Initial triage (severity assessment)
└─ Incident declared if confirmed

Phase 2: Containment (30 min - 2 hours)
├─ Isolate affected systems
├─ Block attacker access
├─ Preserve evidence
├─ Rotate compromised credentials
└─ Notify stakeholders

Phase 3: Investigation (2-24 hours)
├─ Root cause analysis
├─ Scope determination
├─ Timeline reconstruction
├─ Impact assessment
└─ Forensics collection

Phase 4: Eradication (24-48 hours)
├─ Remove malicious code/access
├─ Patch vulnerabilities
├─ Verify clean state
└─ Document changes

Phase 5: Recovery (48-72 hours)
├─ Restore services
├─ Monitor for re-infection
├─ Validate functionality
└─ Gradual rollout

Phase 6: Post-incident (1 week)
├─ Post-mortem meeting (blameless)
├─ Documentation update
├─ Process improvements
├─ Training updates
└─ Customer communication
```

---

## 6.3 План впровадження

### Timeline

```
┌─────────────────────────────────────────────────────────────┐
│ WEEK 1 (P0 - Critical)                                      │
├─────────────────────────────────────────────────────────────┤
│ Day 1-2:                                                    │
│ ├─ Configure branch protection                             │
│ ├─ Setup mandatory MR process                              │
│ └─ Deploy security pipeline                                │
│                                                             │
│ Day 3-5:                                                    │
│ ├─ Train team on GPG signing                               │
│ ├─ Setup CODEOWNERS                                        │
│ └─ Create MR templates                                     │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ WEEK 2-4 (P1 - High)                                        │
├─────────────────────────────────────────────────────────────┤
│ Week 2:                                                     │
│ ├─ Deploy pre-commit hooks                                 │
│ ├─ Setup security dashboard                                │
│ └─ Initial security training                               │
│                                                             │
│ Week 3:                                                     │
│ ├─ Configure alerting                                      │
│ ├─ Document policies                                       │
│ └─ Code review training                                    │
│                                                             │
│ Week 4:                                                     │
│ ├─ Launch Security Champions                               │
│ ├─ Setup incident response                                 │
│ └─ Review and adjust                                       │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ MONTH 2-3 (P2 - Medium)                                     │
├─────────────────────────────────────────────────────────────┤
│ - Advanced security scanning                                │
│ - DAST integration                                          │
│ - Security metrics program                                  │
│ - Gamification rollout                                      │
│ - External security audit                                   │
└─────────────────────────────────────────────────────────────┘
```

### Success Metrics

```
After 1 month:
├─ 100% commits GPG signed
├─ 0 direct pushes to main
├─ 100% MRs go through security checks
├─ < 24h mean time to fix High vulnerabilities
└─ 90%+ team completed security training

After 3 months:
├─ 50% reduction in security findings
├─ < 4h mean time to detect issues
├─ 100% security-critical files have CODEOWNERS
├─ 1 Security Champion per team
└─ 0 Critical vulnerabilities in production

After 6 months:
├─ Security maturity level: 3/5
├─ Zero security incidents
├─ < 1h mean time to detect
├─ Proactive threat hunting
└─ Culture shift: security is everyone's job
```

---

## 6.4 Бюджет та ресурси

**Estimated costs:**

```
One-time investments:
├─ Security tools licenses: $50,000
│  ├─ Snyk: $15K
│  ├─ GitLab Ultimate: $20K
│  └─ Other tools: $15K
│
├─ Training and certification: $30,000
│  ├─ Security training courses: $15K
│  ├─ Certifications: $10K
│  └─ Conference tickets: $5K
│
├─ Consulting (initial setup): $40,000
│  └─ Security audit and setup: $40K
│
└─ TOTAL ONE-TIME: $120,000

Recurring costs (annual):
├─ Tool subscriptions: $60,000
├─ Training budget: $20,000
├─ Security Champion time (20%): $80,000
├─ Bug bounty program: $30,000
└─ TOTAL ANNUAL: $190,000

ROI:
- Cost of prevention: ~$300K (year 1)
- Cost of one breach: $10-15M
- ROI: 3000-5000%
```

**Team resources needed:**

```
Security Team:
├─ 1 Security Engineer (dedicated)
├─ 1 DevSecOps Engineer (50% time)
└─ Security Champions (20% each)

Development Team:
├─ Initial time investment (week 1): 40 hours/dev
├─ Ongoing (per sprint): 4-6 hours/dev
└─ Training: 2 hours/month/dev

Management:
├─ Executive sponsor
├─ Budget approval
└─ Cultural leadership
```
```

---

### Шаблон розділу 7: Формування культури

**Важливо: Конструктивний тон, без звинувачень!**

```markdown
# 7. ФОРМУВАННЯ КУЛЬТУРИ ВІДПОВІДАЛЬНОСТІ

## 7.1 Звернення до команди

Дорогі колеги,

Нещодавній інцидент з коммітом у test_app.py дав нам важливий урок. 
Важливо розуміти: це не про пошук винних, а про нашу спільну можливість 
стати кращими.

Кожен з нас іноді поспішає, пропускає кроки, або просто не знає про 
певні ризики. Це нормально - ми всі люди. Але саме тому ми будуємо 
системи, які нас підстраховують: code review, автоматичні перевірки, 
цифрові підписи. Це не бюрократія заради бюрократії - це наш захисний 
механізм.

Уявіть, ви водій, а безпекові процеси - це ремені безпеки та подушки. 
Більшість часу вони "просто там", але коли щось йде не так - вони 
рятують життя. Так само з аудитом змін: це не перешкода, а страховка.

Наша мета проста: створити середовище, де безпека - це не додаткова 
робота, а природна частина процесу. Де ми допомагаємо один одному, 
де помилки - це можливість навчитися, а не привід для звинувачень.

Тому ми впроваджуємо нові інструменти та процеси. Так, спочатку це 
може здатися незручним. Але як тільки це стане звичкою - ви відчуєте 
спокій: ваш код проходить крізь кілька захисних шарів, і якщо щось 
не так - система підкаже.

Ми всі в одній команді. Безпека - це не "їхня" проблема (Security Team), 
це наша спільна відповідальність. Кожен коміт, кожен review, кожна 
перевірка - це наш внесок у надійність продукту.

Дякую за розуміння та підтримку. Разом ми створимо культуру, де 
безпека та швидкість доповнюють одне одного.

З повагою,
[Ваше ім'я]
Security Team


## 7.2 Принципи культури безпеки

**Що МИ БУДЕМО робити:**

1. **Blameless Post-mortems**
   - Фокус на системі, не на людях
   - "Що пішло не так?" замість "Хто накосячив?"
   - Документуємо уроки, не покарання

2. **Shared Responsibility**
   - Безпека = завдання КОЖНОГО
   - Security Team = enablers, not gatekeepers
   - Помилки = можливість для growth

3. **Continuous Learning**
   - Регулярні security brown bags
   - Sharing knowledge, not blame
   - Celebratе security wins

4. **Empowerment**
   - Дати tools та training
   - Security Champions в кожній команді
   - Voice concerns без страху

5. **Balance Speed & Security**
   - Автоматизація замість бюрократії
   - Security as code
   - Shift left, not slow down

**Що МИ НЕ БУДЕМО робити:**

❌ Blame individuals for mistakes
❌ Create fear-based culture
❌ Make security a blocker by default
❌ Hide incidents or learnings
❌ Punish people for raising concerns

**Measurement of success:**

- Psychological safety score
- Number of proactive security reports
- Team satisfaction with security process
- Time to implement security fixes
- Knowledge sharing metrics
```

---

### Шаблон розділу 8: Висновки

```markdown
# 8. ВИСНОВКИ

## 8.1 Ключові висновки

Аналіз інциденту з коммітом у test_app.py виявив критичні недоліки 
в наших процесах контролю змін. Основні висновки:

### 1. Технічний рівень

**Проблеми:**
- Відсутність branch protection дозволила direct push у main
- Code review не був обов'язковим
- CI/CD перевірки спрацьовували ПІСЛЯ merge
- Цифрові підписи не використовувалися

**Результат:** Критичні вразливості (eval, exec, hardcoded secrets) 
потрапили в main гілку, creating significant risk.

### 2. Процесний рівень

**Проблеми:**
- Відсутність формальних політик SCM
- "Швидкість понад безпеку" ментальність
- Недостатня автоматизація security checks
- Alert fatigue (SAST warnings ignored)

**Результат:** Multiple defense layers failed, створивши "Swiss cheese" 
ефект, де vulnerability пройшла всі бар'єри.

### 3. Культурний рівень

**Проблеми:**
- Безпека = "завдання Security Team"
- Відсутність shared responsibility
- Lack of security awareness
- Fear of "slowing down" development

**Результат:** Навіть при наявності tools, культура не підтримувала 
їх використання.

---

## 8.2 Важливість аудиту в SSDLC

**Чому аудит змін критичний:**

1. **Verification of Integrity**
   - Доказ того, що код створено тими, хто заявлений
   - Виявлення компрометованих акаунтів
   - Non-repudiation для compliance

2. **Early Detection**
   - Виявлення проблем до production
   - Shift Left Security принцип
   - Cost reduction (fix early = дешевше)

3. **Compliance Requirements**
   - SOC 2, ISO 27001, PCI DSS вимагають
   - Audit trails для regulatory
   - Evidence для certifications

4. **Supply Chain Security**
   - Захист від malicious code injection
   - Verification of dependencies
   - Trust but verify approach

5. **Knowledge Sharing**
   - Code review = learning opportunity
   - Best practices propagation
   - Team skill development

**Статистика галузі:**
- 70% вразливостей виявляються під час code review
- Organizations з strong audit processes мають 60% fewer breaches
- Cost of fixing post-production: 30x більше ніж at development

---

## 8.3 Roadmap на майбутнє

### Short-term (1-3 місяці)

**Фундація:**
```
✅ Branch protection rules enforced
✅ Mandatory code review process
✅ GPG signing required
✅ Pre-merge security checks
✅ CODEOWNERS implemented
✅ Security training completed
```

**Metrics:**
- 100% commits signed
- 0 direct pushes to main
- < 24h High vulnerability fix time

---

### Mid-term (3-6 місяців)

**Automation & Culture:**
```
✅ Pre-commit hooks deployed
✅ Security Champions program active
✅ Automated security dashboard
✅ Incident response procedures tested
✅ Advanced SAST/DAST integration
```

**Metrics:**
- 50% reduction in findings
- 90%+ developer satisfaction
- 1 Security Champion per team

---

### Long-term (6-12 місяців)

**Maturity & Excellence:**
```
✅ Zero-trust architecture
✅ Continuous threat modeling
✅ Proactive vulnerability management
✅ Security as competitive advantage
✅ Industry recognition (certifications)
```

**Metrics:**
- Security maturity level 4-5/5
- Zero critical incidents
- Best-in-class security posture

---

## 8.4 Фінальний висновок

Цей інцидент - не failure, а **wake-up call та opportunity**. 

Ми маємо шанс перетворити наш development process на industry-leading 
security practice. З правильними tools, processes, та culture ми можемо 
досягти:

- **Швидкість** через автоматизацію (не уповільнення)
- **Безпеку** через defense in depth
- **Якість** через continuous improvement
- **Довіру** через transparency та responsibility

Шлях буде непростим, але інвестиція в безпеку сьогодні - це захист 
нашого майбутнього. Кожен з нас грає роль у цій трансформації.

**Наступні кроки:**
1. Review and approve цю стратегію
2. Allocate resources (budget, people, time)
3. Start implementation (week 1 priorities)
4. Monitor progress and adjust
5. Celebrate wins and learn from setbacks

Разом ми побудуємо security culture, де якість та швидкість йдуть пліч-о-пліч.

---

**Підготував:** [Ваше ім'я]  
**Дата:** [Дата]  
**Версія:** 1.0  
**Статус:** Draft / Final  
```

---

## 📊 Критерії оцінювання (приблизні)

| Критерій | Бали | Що оцінюється |
|----------|------|---------------|
| **Опис зміни та технічний аналіз** | 25 | Використання даних з лабораторної, детальність, структурованість |
| **Виявлення порушень та аналіз** | 20 | Повнота переліку, глибина аналізу, зв'язок з SSDLC |
| **Реалістичність сценарію** | 20 | Правдоподібність, деталізація, timeline, наслідки |
| **Якість превентивної стратегії** | 20 | Конкретність заходів, технічні+організаційні, план впровадження |
| **Культура та комунікація** | 10 | Конструктивність, відсутність звинувачень, мотивація команди |
| **Структура та оформлення** | 5 | Логічність, читабельність, дотримання формату |
| **ЗАГАЛОМ** | 100 | |

---

## ✅ Чеклист перед здачею

### Контент:
- [ ] Всі 8 розділів присутні
- [ ] Використані дані з лабораторної роботи
- [ ] Моделювання інциденту реалістичне та детальне
- [ ] Превентивна стратегія містить конкретні заходи
- [ ] Звернення до команди конструктивне
- [ ] Висновки підсумовують всю роботу

### Технічна частина:
- [ ] Перелічені ВСІ порушення з лабораторної
- [ ] Пояснено ЯК кожне порушення створює ризик
- [ ] Показано зв'язок з SSDLC принципами
- [ ] Наведені конкретні технічні рішення
- [ ] Є timeline впровадження

### Сценарій інциденту:
- [ ] Чіткий timeline подій
- [ ] Показано ланцюг від коміту до breach
- [ ] Пояснено чому не виявлено раніше
- [ ] Розписані наслідки (users, business, team)
- [ ] Є lessons learned

### Культурна частина:
- [ ] Звернення без звинувачень
- [ ] Фокус на спільну відповідальність
- [ ] Конструктивний тон
- [ ] Мотивація до змін
- [ ] Довжина до 200 слів

### Оформлення:
- [ ] Структура відповідає вимогам
- [ ] Обсяг 2-3 сторінки
- [ ] Є таблиці/діаграми де потрібно
- [ ] Скриншоти додані (якщо є)
- [ ] Посилання на коміти

---

## 💡 Поради для успішного виконання

### 1. Використовуйте лабораторну як базу
- Перенесіть ВСІ технічні факти
- Розширте кожне порушення аналізом "чому ризик"
- Додайте зв'язок з SSDLC

### 2. Зробіть сценарій реалістичним
- Базуйте на реальних кейсах (SolarWinds, etc.)
- Конкретні цифри (вартість breach)
- Реальний timeline (не "щось десь колись")

### 3. Будьте конкретними в рішеннях
- Не "покращити безпеку", а "встановити branch protection з такими-то параметрами"
- Конкретні інструменти, команди, конфігурації
- Реалістичний timeline та бюджет

### 4. Культура = ключ до успіху
- Пам'ятайте: люди >>> процеси >>> інструменти
- Без культури навіть найкращі tools не працюють
- Звернення має надихати, а не лякати

### 5. Структурованість
- Використовуйте таблиці, списки, діаграми
- Логічні переходи між розділами
- Кожен розділ має висновок

---

## 📚 Корисні ресурси

- [OWASP SAMM](https://owaspsamm.org/) - Security maturity model
- [Microsoft SDL](https://www.microsoft.com/en-us/securityengineering/sdl) - SSDLC framework
- [GitLab Security Best Practices](https://docs.gitlab.com/ee/security/)
- [NIST Secure Software Development Framework](https://csrc.nist.gov/publications/detail/sp/800-218/final)
- [Awesome DevSecOps](https://github.com/TaptuIT/awesome-devsecops) - Tools and resources

---

**Успіхів у виконанні домашнього завдання! 🛡️🚀**

Це ваш шанс показати стратегічне мислення та здатність переходити від 
технічного аналізу до комплексних бізнес-рішень.
