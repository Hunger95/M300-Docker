# Dokumentation Docker Modul 300 (LB3)

## von Cédric Droz

Dies ist eine Dokumentation zur Arbeit im Modul 300 über Docker von Cédric Droz.



## Vorgehen:

Als erstes werde ich mal folgendes Tutorial durchmachen, um mich mit Docker zu beschäftigen und dieses auch zu studieren:

<https://docs.docker.com/get-started>



Nachdem ich mich nun informiert habe, werde ich definieren, was ich mit Docker in betrieb nehmen will:



Geplant ist, dass ich wie bei der Vagrant Aufgabe einen LAMP-Stack containerisiere. Dazu gehört ein Docker image welches einen Webserver und noch eine MySQL Datenbank aufsetzt. Weiter werde ich dazu noch ein phpmyadmin entsprechend einrichten, was aus einem anderen Image kommt, um die Kompetenz der Kombination von zwei verschiedenen Containern zu bekommen.

Weiter werde ich ein entsprechendes persistentes Volume für die DB erstellen und Sicherheitsmasnahmen und Monitoring umsetzen.



## Vorwissen:

Neben der grösseren Erfahrung mit Linux durch mein Lehrbetrieb bin ich auch aktuell im Team Platform tätig. Dort bekomme ich einen Einstieg in die Arbeit mit Openshift und Kubernetes. Also nicht direkt mit Docker aber sehr ähnlichen und verwandten Produkten. Trotz meinem Aufenthalt in dieser Abteilung, weiss ich noch relativ wenig zu den verschiedenen Container-Programmen und Konzepten. Mit Openshift, kann ich mittlerweile einige Operationen durchführen und das Monitoring kenne ich auch ein bisschen. Technisch, weiss ich jedoch nicht sehr viel über unsere Containerplattform. 



## Verwendete Tools:

- Visual Studio Code - für die bearbeitung der verschiedenen Files wie z.B. Dockerfile
- Typora - für die Bearbeitung von diesem Mark Down File
- Git client - für den Sync zwischen der lokalen Maschine und dem eigenen Git-Repo



## Sicherheit:

Die Sicherheit ist bei meinem Docker Projekt mit folgenden Punkten gewährleistet:

- CPU Leistung begränzen
- Neustarts begränzen
- Überwachung und Benachrichtigungen
- Syslog Einbindung



## Funktionsweise/Tests:

Die Funktionsweise des Container-Setups wurde natürlich auch geprüft nach anlegen der Container.

Die folgenden Tests, habe ich durchgeführt um die Kommunikation zwischen den verschiedenen Containern zu prüfen:

- Kann auf den Webserver per "localhost:80" zugegriffen werden?
- Ist die Datenbank ansprechbar über Phpmyadmin?
- Werden die Änderungen in MySQL auch persistent im angelegten Volume gespeichert?
- Funktioniert die Überwachung der Container wie erwartet?
- Wurden die CPU und Memory Limits angewandt?



Die Tests können alle durch das Webgui des Webservers, der Datenbank und des Monitoring geprüft werden.

Hier eine Tabelle mit den Ergebnissen:



| **Test Punkt**                                               | **Erwartetes Ergenis**                                       | **Tatsächliches Ergebnis** |
| ------------------------------------------------------------ | ------------------------------------------------------------ | -------------------------- |
| Webserver erreichbar unter localhost                         | default Webseite gibt MySQL Verbindungsstatus zurück         | Funktioniert!              |
| MySQL über Phpmyadmin erreichbar                             | PhpMyAdmin login funktioniert mit MySQL Env-Variabeln        | Funktioniert!              |
| Testdatenbank (im GUI erstellt) ist über SQL ersichtlich nach einem Neustart | Nach Neustart ist im GUI neu erstellte DB per SQL aufgelistet | Funktioniert!              |
| Monitoring per CAdvisor ist im Webbrowser erreichbar und gibt realistische Werte aus | CAdvisor kann erreicht werden und kann mit InfluxDB kommunizieren | Funktioniert!              |
| Im Monitoring wird auch bei Belastung nicht mehr CPU oder Memory Usage angezeigt als die gesetzten Werte | In CAdvisor gibt es keine Container, welche über die Limite CPU oder Memory braucht | Funktioniert!              |



## Reflexion/Wissenszuwachs:

Da ich im Geschäft wie bereits erwähnt momentan mit Docker-ähnliche Plattformen zu tun habe, war der Container-Einstieg im allgemeinen stark verkürzt. Somit konnte ich mit einem gewissen Vorwissen bezüglich Container an diese Aufgabe gehen, was mir eigentlich nur noch die Docker-Spezifik und die technische Umsetzung lies.

Diese LB hat mir erstaunlicher weise ziemlich viel Spass gemacht. Wenn ich ehrlich bin, hatte ich einige Tage, an denen ich mit Docker ein bisschen zu kämpfen hatte und desswegen nicht der produktivste im Unterricht war. Als ich dann jedoch nach einigen Erfolgsergebnissen motiviert mich auf die Arbeit konzentrieren konnte, war dann der Rest des Setups nur noch ein reibungsloser ablauf. Mit einer neuen Technologie direkt zurecht zu kommen ist für mich eigentlich ein grösseres Problem, was ich jedoch nicht bei dieser Arbeit merkte.

Ich habe somit viel neues über Containerisierung und noch viel mehr über Docker spezifisch durch gute Anleitungen und Erklärungen aus dem Internet gelernt.