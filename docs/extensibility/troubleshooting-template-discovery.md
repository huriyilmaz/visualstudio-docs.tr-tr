---
title: Visual Studio'da sorun giderme şablonu bulma | Microsoft Dokümanlar
ms.date: 01/02/2018
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 078d06c797c3b228c1ea5b1d836dceb0394b3174
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698927"
---
# <a name="troubleshooting-template-installation"></a>Sorun giderme şablonu yükleme

Projenizi veya madde şablonlarınızı dağıtan sorunlarla karşınıza çıkarsa, tanıgünlüğe kaydetmeyi etkinleştirebilirsiniz.

::: moniker range="vs-2017"

1. Yüklemeniz için *Common7\IDE\CommonExtensions* klasöründe bir pkgdef dosyası oluşturun. Örneğin, *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefC.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Yüklemeniz için *Common7\IDE\CommonExtensions* klasöründe bir pkgdef dosyası oluşturun. Örneğin, *C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefC.pkgdef*.

::: moniker-end

2. pkgdef dosyasına aşağıdakileri ekleyin:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Yüklemeniz ve çalıştırmanız `devenv /updateConfiguration`için bir Geliştirici Komut Komut [Ustem'i](/dotnet/framework/tools/developer-command-prompt-for-vs) açın.

::: moniker range="vs-2017"

4. Visual Studio'yu açın ve her iki şablon ağacını başlatmak için Yeni Proje ve Yeni Öğe iletişim kutularını başlatın.

   Şablon günlüğü artık **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** içinde görünür (instanceid, Visual Studio örneğinizin yükleme kimliğine karşılık gelir). Her şablon ağacı başlatma bu günlük girişleri ekler.

::: moniker-end

::: moniker range=">=vs-2019"

4. Visual Studio'yu açın ve her iki şablon ağacını başlatmak için yeni bir proje ve **Yeni Öğe** iletişim kutuları **oluşturun.**

   Şablon günlüğü artık **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_[instanceid]\VsTemplateDiagnosticsList.csv** içinde görünür (instanceid, Visual Studio örneğinizin yükleme kimliğine karşılık gelir). Her şablon ağacı başlatma bu günlük girişleri ekler.

::: moniker-end

Günlük dosyası aşağıdaki sütunları içerir:

- **FullPathToTemplate**, aşağıdaki değerlere sahiptir:

  - Bildirim tabanlı dağıtım için 1

  - Disk tabanlı dağıtım için 0

- **TemplateFileName**

- Diğer şablon özellikleri

> [!NOTE]
> Günlüğe kaydetmeyi devre dışı kaldırmak için, pkgdef `EnableTemplateDiscoveryLog` dosyasını kaldırın veya `dword:00000000`değerini değiştirin ve sonra yeniden çalıştırın. `devenv /updateConfiguration`

## <a name="see-also"></a>Ayrıca bkz.

- [Özel proje ve öğe şablonları oluşturma](creating-custom-project-and-item-templates.md)
