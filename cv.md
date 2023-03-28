# rsschool-cv
## Ivan Khimich / Junior Software Developer

### Contacts
* __Address:__ Serbia, Belgrade
* __Email:__ himivan@gmail.com
* __LinkedIn:__ [Ivan Khimich](https://www.linkedin.com/in/%D0%B8%D0%B2%D0%B0%D0%BD-%D1%85%D0%B8%D0%BC%D0%B8%D1%87-19644b90/)
* __Telegram:__ https://t.me/kudraem
* __GitHub:__ https://github.com/kudraem/
* __Phone:__ +7 (747) 871-95-19
* __Twitter:__ [@kudraem](https://twitter.com/kudraem)

### Briefly About Myself
I’m currently working on freelance - fullstack web developer and learning Computer Science.

I want to be a professional developer with fundamental knowledge and professional skills that will allow me to create high quality software.
I love to write, read, test code and problem solving.

I’m looking to job. 

Fun fact: retired lawyer.

### Skills
- Python / Django
- PHP / Laravel
- HTML / CSS / Sass
- JavaScript / Vue.js / Node.js
- Bitrix24
- Git / GitHub / GitLab
- Bash / Zsh
- Mysql / PostgreSQL / MongoDB

### Work Experience
#### Freelance / 2020 - 2023
Fullstack web developer. I've developed simple UI (dashboards, admin panels, forms, etc.), microservices, integration with different REST API services, workflows automatization.

There are some projects:
1. [Bitrix24 Call Automatization Tool](https://gitlab.com/kudraem/b24_missed_call_activity_autoclose/)
1. [aff-lead.com PHP API Wrapper](https://gitlab.com/kudraem/aff-lead.com-api/)

### Education
1. Southern Federal University, Faculty of Law, Specialist degree / 2010 - 2015
1. Coursera / Course "Introduction to Git and GitHub"
1. EdX / Course "How to Code: Simple Data"
1. EdX / Course "How to Code: Complex Data"
1. MIT OCW / Course "6.0001 Introduction to Computer Science and Programming in Python"

### Languages
* English - B1 (Intermediate) CEFR Level
* Russian - native speaker

### Code Example
```php
<?php

require_once __DIR__ . '/AffLeadApiException.php';

class AffLeadApi {
    private $apiToken;
    private $baseUrl = 'https://aff-lead.com/lion';

    public function __construct($apiToken)
    {
        $this->apiToken = $apiToken;
    }

    public function request($method, $params)
    {
        $url = sprintf("%s/%s", $this->baseUrl, $method);

        $params['Token'] = $this->apiToken;

        $ch = curl_init($url);
        curl_setopt($ch, CURLOPT_POST, true);
        curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($params));
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

        $response = curl_exec($ch);

        if (curl_errno($ch)) {
            throw new \Exception(curl_error($ch), 1);
        }

        $httpCode = curl_getinfo($ch, CURLINFO_HTTP_CODE);
        if ($httpCode != 200) {
            $exceptionMessage = sprintf('http code - %s', $httpCode);
            throw new \Exception($exceptionMessage, 1);
        }

        $result = json_decode($response, true, 512, JSON_THROW_ON_ERROR);
        curl_close($ch);

        return $result;
    }
}
```