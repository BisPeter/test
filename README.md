## Azure monitor
Im preview unterstützt die standard format mit open Telemetry.
Im großem sinne geht alles in diese richtung.

Im Azure Monitor werden Metric Daten verwendet (counts von .Net oder counts die man selber generiert).
Außerdem werden Log Informationen auch verwendet.

Diese beiden Daten kommen einerseids unsere Applikation kann aber auch von dem Betribsystem, Azure Services.

Metriks und logs kann mann über Insights nutzen.
* Applikation		
* Container
* VM

Diese informationen (Metriks und Logs) können auch Visualisiert werden.

* Im Dashboards
* Über Power BI können Analysiert werden.
* im Workbook diverse Charts definieren.

Die Daten aus Metriks und Logs können Analysiert werden.
* Mit Metric Analystics
* Mit Log Analytics

Es kann auf die Metriken und Logs reagiert werden.
* Automathische skalierung anhand der Metrik
* Alerts erstellen

Es kann auch in diversen sachen integriert werden:
* Event Hubs
* Logic Apps
* Exportieren für analyse
	
## ALERTS
Alerts basieren auf Notifikationen an bestimmten Bedingungen. 
Alerts sind einheitlich über verschiedene Services wie Applikation insights, Log Analytics oder Azure Monitor. 
Alerts können auf viele verschieden Metriken angebunden werden. 
Es können HealthChecks sein, File system benutzung oder CPU Zeit und vieles mehr. 
Z.b. wenn der CPU zeit größer als eine bestimmte wert aber es kann auch auf eine treshhold Sensitivity angebunden sein. 
Es kann ausgesucht werden was es passieren soll wenn die kondition eintrifft. Es kann unter anderem ein SmS aber auch ein E-mail Sein. 
Außerdem kann ein Action auch ausgeführt weden, ein  Logic app gestartet werden oder eine Webhook aufgerufen weden. 

## Application Insights
Beim Applikation Insights werden die bisher angesprochenen Loginformation (Metriks und Logs) gesammelt (können aber zuzätzlich auch Telemetry Daten genutzt werden).

Es ist möglich Application Insights in Azure bei eine Webapplikation zu Aktivieren.
Je nach verwendeten Framework erfolgt es auch aber automatisch, ansonsten muss es im Apllikation explizit hingefügt/referenzieren werden.

Es ist aber auch möglich diese Insights Client seitig zu verwenden.
Es kann beispielweise in eine JavaScript library oder auch in eine WPF Applikation verwendet werden können.
In eine WbApplikation muss es in der startup Klasse beim konfiguerieren der Services hingefügt werden.
Die InstumentationsKey kann gleich beim hinfügen der appinsight oder in der Appsettings auch definiert werden.
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
Mit der Klasse ApplikationInsightsServiceOptions, kann die ApplikationInsightsTelemetry Konfigureiert werden.

Man kann entweder ApplikationsInsightsTelemetry Objekte injecten und da Informationen reinschreiben oder die normale Logging verwenden.


Applikation Insights kann bei eigenen Applikationen explizit aktiviert werden. (Z.b.: Server applikationen, WPF appllikationen, JavaScript Apllikationen)
All diese Informationen werden zur Azure Applikation Insights geleitet um die in verschieden Arten nutzen zu können.
Datenbank zugriffe werden zum Beispiel auch automatisch geloggt.

Beim Apllikations Insights kann auch arificial Intelligence verwendet  werden.
Beim Azure heißt es Cognitive Services.
Diese Services behandeln zum Beispiel Text to speech, Speech to text, Bilderkennung sowie Anomaly Detection.
Die Anomaly detection wird zum Beispiel auch verwendet um die applikation zu Monitoren.
Zum Beispiel wenn der Applikation sich nicht regelmäßig verhält können Benachrichtigungen versendet werden.

## Applikation Map

Eine Applikation map stellt dar welche Services mit was kommunizieren.
Es hilft eine bessere überblick zu geben wo, bei welchen Applikation Problemem gegeben hat.
Es kann aber beim finden der Urschen der fehler helfen.
Es kann aber auch abgelesen werden welche Requests die langsamsten waren.
Es wird zum beispiel angezeigt wie viele Calls zu eine Service getetigt wurden und wie viel Prozent dieser Calls fehlerhaft war.


## Visual Studio App Center

Man kann Client seitige Applikationen registrieren.
Es stellt eine Build environment zu verfügung.
Man kann die Pplikationen auf verschiedene Geräten testen.
Die Applikation kann verteilt werden für verschiedene Gruppen (Für beta test zum Beispiel).
Außerdem können zum Bispiel Analyse informationen abgerufen werden.

