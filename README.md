

## Azure Monitor
Be dem Azure Monitor wird bereits im Preview das Standardformat mit Open Telemetry unterstützt.
Im Großen und Ganzen geht alles in die Richtung Open Telemetry.

Im Azure Monitor werden Metric Daten verwendet (Counts von .Net oder Counts die man selber generiert).
Außerdem werden auch Log Informationen verwendet.

Diese beiden Daten können einerseits aus unserer Applikation kommen, sie können aber auch von dem Betriebsystem oder von Azure Services kommen.

Metrics und Logs kann mann über Insights nutzen:
* Applikation		
* Container
* VM

Diese Informationen (Metrics und Logs) können auch visualisiert werden:
* In Dashboards
* Über Power BI können sie analysiert werden
* Im Workbook können diverse Charts definiert werden

Die Daten aus Metrics und Logs können analysiert werden:
* Mit Metric Analystics
* Mit Log Analytics

Es kann auf die Metrics und Logs reagiert werden:
* Mit automatischer Skalierung anhand der Metric
* Es können auch Alerts erstellen werden

Azure Monitor kann auch in diversen Sachen integriert werden:
* Event Hubs
* Logic Apps
* Exportieren für Analyse
	
## ALERTS
Alerts basieren auf Notifikationen, die durch bestimmte Bedingungen ausgelöst werden. 
Alerts sind einheitlich in den verschiedenen Services wie Applikation Insights, Log Analytics oder Azure Monitor. 
Alerts können an viele verschiedene Metriken angebunden werden. 
Es können HealthChecks sein, File System Benutzung oder CPU Zeit und vieles mehr. 
Ein Beispiel für das Anbinden an eine Metrik wäre, wenn die CPU Zeit größer ist als ein bestimmter Wert. 
Es kann ausgesucht werden was passieren soll wenn die Bedingung eintrifft. Es kann unter anderem eine SmS aber auch eine E-mail verschickt werden. 
Außerdem kann auch eine Action ausgeführt weden, eine Logic App gestartet werden oder ein Webhook aufgerufen weden. 

## Application Insights
Bei Application Insights werden die bisher angesprochenen Loginformation (Metriks und Logs) gesammelt (es können aber zuzätzlich auch Telemetry Daten genutzt werden).

Es ist möglich Application Insights in Azure bei einer Webapplikation zu aktivieren.
Je nach verwendetem Framework erfolgt es aber auch automatisch, ansonsten muss es in der Apllikation explizit hingzuefügt/referenziert werden.

Es ist aber auch möglich, die Insights Client-seitig zu verwenden.
Application Insights können beispielweise in einer JavaScript library oder auch in eine WPF Applikation verwendet werden.
In einer WebApplikation muss es in der Startup Klasse beim Konfigurieren der Services hinzugefügt werden.
Der InstumentationsKey kann gleich beim Hinzufügen der Appinsight oder auch in den Appsettings definiert werden.
```C#
 public void ConfigureServices(IServiceCollection services)
        {
            services.AddRazorPages();
            services.AddDbContext<BooksContext>(options =>
            {
                var connectionString = Configuration.GetConnectionString("BooksConnection");
                options.UseSqlServer(connectionString);
            });

  /*--->*/  services.AddApplicationInsightsTelemetry(/*InstrumentationKey*/); /*<---*/
        }
```	
Mit der Klasse ApplikationInsightsServiceOptions, kann die ApplikationInsightsTelemetry konfiguriert werden.

Man kann entweder ApplikationsInsightsTelemetry Objekte injecten und dort die Informationen reinschreiben oder das normale Logging verwenden.


Application Insights kann bei eigenen Applikationen explizit aktiviert werden. (Z.b.: Server Applikationen, WPF Appllikationen, JavaScript Apllikationen)
All diese Informationen werden zur Azure Applikation Insights geleitet um diese in verschieden Arten nutzen zu können.
Datenbankzugriffe werden zum Beispiel auch automatisch geloggt.

Bei Apllications Insights kann auch künstliche Intelligenz verwendet werden.
Bei Azure heißt es Cognitive Services.
Diese Services behandeln zum Beispiel Text to Speech, Speech to Text, Bilderkennung sowie Anomaly Detection.
Die Anomaly Detection wird zum Beispiel auch verwendet um die Applikationen zu monitoren.
Zum Beispiel wenn sich die Applikation nicht regelmäßig verhält, können Benachrichtigungen versendet werden.

## Application Map

Eine Application Map stellt dar, welche Services mit was kommunizieren.
Es hilft einen besseren Überblick zu geben wo, bei welchen Applikationen es Probleme gegeben hat.
Es kann aber beim Finden der Ursachen der Fehler helfen.
Es kann aber auch abgelesen werden, welche Requests die Langsamsten waren.
Es wird zum Beispiel angezeigt, wie viele Calls zu einem Service getätigt wurden und wie viel Prozent dieser Calls fehlerhaft waren.


## Visual Studio App Center

Man kann Client-seitige Applikationen registrieren.
Es stellt ein Build Environment zu Verfügung.
Man kann die Applikationen auf verschiedenen Geräten testen.
Die Applikation kann an verschiedene Gruppen verteilt werden (Für beta test zum Beispiel).
Außerdem können zum Beispiel Analyseinformationen abgerufen werden.




## Cosmos Datenbank
Azure Cosmos DB ist eine no sequel Datenbank.
In Azure ist es möglich ein API Option auszusuchen. Unter anderem Core (SQL), Cassandra, PostgreSQL, Azure Cosmos DB API für MongoDB.
Wenn auf die Datenbank mit Entity Framework zugegriffen wird, ist man gezwungen Core (SQL) zu wählen. Da werden einfach json Objekte gespeichert.
Anstatt eines Datenbank Schemas wird ein Container verwendet.
Ein Beispiel dazu ist eine Menükarte mit Items darin.
In einer relationalen Datenbank würde man eine Tabelle für Menükarten erstellen und eine Tabelle für die Menü Items.
In der Cosmos Datenbank kann man die Items direkt in der Menükarte speichern.

Es wird wie folgt erstellt:
```C#
 modelBuilder.HasDefaultContainer("menucards"); 
 modelBuilder.Entity<MenuCard>().OwnsMany(c => c.MenuItems); 
 modelBuilder.Entity<MenuCard>().HasKey(c => c.MenuCardId);
```

## Active Directory
In Azure kann man Active Directorys erzeugen.
In unserem Beispiel wurde ein B2C verwendet.
Hier kann mann Applikationen registrieren und Identity Provider registrieren (der Benutzer kann z.B. seinen Amazon Account mitnehmen).
* Es können User Informationen gespeichert werden.
* Man kann Benutzer registrieren.
* Man kann User Flows definieren.
