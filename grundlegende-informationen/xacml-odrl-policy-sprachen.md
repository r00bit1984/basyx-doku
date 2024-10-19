---
icon: building-shield
---

# XACML/ODRL (Policy-Sprachen)

## XACML

_(eXtensible Access Control Markup Language)_

* XML-Schema für die Darstellung und Verarbeitung von Autorisierungs-Policies
* ist für attributbasierte Zugriffskontrolle
* aus den Policies werden Zugangsrichtlinien erstellt
* beschreibt, wie man Zugangsanfragen behandeln soll

### Regeln und Policies

* Eine Regel besteht aus mehreren Voraussetzungen.
* Eine Regel beschreibt die Zugangsgewährung.
* Wenn eine Voraussetzung nicht ausgewertet werden kann, dann ist die Regel unbestimmt.
* Alle Regeln zusammen sind eine Policy.
* Policysets sind mehrere Policies bzw Policysets, bilden eine Hierarchie
* Policies und Regeln sind frei kombinierbar

### Syntax

Beispiel:

```XACML
<Rule RuleId="f6637b3f-3690-4cce-989c-2ce9c053d6fa" Effect="Deny">
	<Description>Use it or lose it: this policy denies access if lastLogin is more than 30 days away from today's date</Description>
	<Target/>
	<Condition>
		<Apply FunctionId="urn:oasis:names:tc:xacml:1.0:function:any-of">
			<Function FunctionId="urn:oasis:names:tc:xacml:1.0:function:dateTime-greater-than"/>
		</Apply>
	</Condition>
</Rule>
```

#### Quellen

* [https://en.wikipedia.org/wiki/XACML](https://en.wikipedia.org/wiki/XACML)

## ODRL

_(Open Digital Rights Language)_

* Beschreibt die grundlegenden Konzepte, Entitäten und Beziehungen
* tätigt Aussagen über die Nutzung digitaler Güter
* W3C-Empfehlung zur Verbesserung der Funktionalität und Kompatibilität des Webs.

### Syntax

Beispiel (ähnelt JSON):

```json
{
 "@context": "http://www.w3.org/ns/odrl.jsonld",
 "uid": "http://example.com/policy:001",
 "permission": [{
 	"target": "http://example.com/mysong.mp3",
	"assignee": "John Doe",
	"action": "play"
 }]
}
```

#### Quellen

* [https://en.wikipedia.org/wiki/ODRL](https://en.wikipedia.org/wiki/ODRL)
* [https://www.w3.org/TR/odrl-model/](https://www.w3.org/TR/odrl-model/)
* Kebede, M.G., Sileno, G., Van Engers, T. (2021). A Critical Reflection on ODRL. In: Rodríguez-Doncel, V., Palmirani, M., Araszkiewicz, M., Casanovas, P., Pagallo, U., Sartor, G. (eds) AI Approaches to the Complexity of Legal Systems XI-XII. AICOL AICOL XAILA 2020 2018 2020. Lecture Notes in Computer Science(), vol 13048. Springer, Cham. https://doi.org/10.1007/978-3-030-89811-3\_4
