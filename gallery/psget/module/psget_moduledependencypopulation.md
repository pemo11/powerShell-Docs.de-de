---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: "Logik zum Vorbereiten der Modulabhängigkeiten während des Veröffentlichungsvorgangs | MSDN"
ms.openlocfilehash: 126cd65ac35a31f4118474bc36dac1836ec0f22e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a>Logik zum Vorbereiten der Modulabhängigkeiten während des Veröffentlichungsvorgangs
1.  Module, die als Teil von RequiredModules aufgelistet sind, werden als Abhängigkeiten betrachtet.
2.  Module, die als Teil des NestedModules-Schlüssels aufgelistet sind, dessen Modulbasis nicht Teil der angegebenen Modulbasis ist, werden als Abhängigkeiten betrachtet.

3.  Abhängigkeiten sollten in erster Linie auf dem gleichen Zielrepository vorhanden sein, ansonsten wird für den Veröffentlichungsvorgang ein Fehler ausgegeben.
    Zum Beispiel: Wenn „SnippetPx“ nicht auf dem Repository verfügbar ist, wird der unten dargestellte Fehler ausgegeben.
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  Einige Modulabhängigkeiten können extern verwaltet werden. In diesem Fall müssen sie dem Eintrag ExternalModuleDependencies im PSData-Abschnitt des Modulmanifests hinzugefügt werden.
    Im Folgenden ist ein Teil der oben angezeigten Fehlermeldung dargestellt.
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

*Während der Modulinstallation wird die oben dargestellte vorbereitete Liste der Abhängigkeiten für die Installation der Abhängigkeiten verwendet.*

*Stellen Sie sicher, dass die Abhängigkeiten Ihres Moduls unter „$env:PSModulePath“ auf Ihrem System während der Veröffentlichung verfügbar sind.*

