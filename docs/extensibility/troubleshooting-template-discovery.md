---
title: Visual Studio 'da şablon bulma sorunlarını giderme | Microsoft Docs
description: Visual Studio SDK 'da özel proje ve şablon dağıtma sorunlarını gidermek için tanılama günlüğünü etkinleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 82b7b3f5eced4c8e24830fba34e47d224186949d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072955"
---
# <a name="troubleshooting-template-installation"></a>Şablon yükleme sorunlarını giderme

Projenizi veya öğe şablonlarınızı dağıtmaya yönelik sorunlarla karşılaşırsanız, tanılama günlüğünü etkinleştirebilirsiniz.

::: moniker range="vs-2017"

1. Yüklemenizin *Common7\IDE\CommonExtensions* klasöründe bir pkgdef dosyası oluşturun. Örneğin, *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Yüklemenizin *Common7\IDE\CommonExtensions* klasöründe bir pkgdef dosyası oluşturun. Örneğin, *C:\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Aşağıdakileri pkgdef dosyasına ekleyin:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Yüklemeniz için bir [Geliştirici komut istemi](../ide/reference/command-prompt-powershell.md) açın ve çalıştırın `devenv /updateConfiguration` .

::: moniker range="vs-2017"

4. Visual Studio 'Yu açın ve yeni proje ve yeni öğe iletişim kutularını başlatarak her iki şablon ağacının de başlatılmasını sağlar.

   Şablon günlüğü artık **%LocalAppData%\microsoft\visualstudio\15.0_ [InstanceId] \VsTemplateDiagnosticsList.csv** (InstanceId, Visual Studio ÖRNEĞINIZIN yükleme kimliğine karşılık gelir) içinde görüntülenir. Her şablon ağacı başlatma, girdileri bu günlüğe ekler.

::: moniker-end

::: moniker range=">=vs-2019"

4. Visual Studio 'Yu açın ve her iki şablon ağacının başlatılması için **Yeni proje** ve **Yeni öğe** oluştur iletişim kutularını başlatın.

   Şablon günlüğü artık **%LocalAppData%\microsoft\visualstudio\16.0_ [InstanceId] \VsTemplateDiagnosticsList.csv** (InstanceId, Visual Studio ÖRNEĞINIZIN yükleme kimliğine karşılık gelir) içinde görüntülenir. Her şablon ağacı başlatma, girdileri bu günlüğe ekler.

::: moniker-end

Günlük dosyası şu sütunları içerir:

- Aşağıdaki değerlere sahip olan **Fullpathtotemplate**:

  - 1 bildirim tabanlı dağıtım için

  - disk tabanlı dağıtım için 0

- **TemplateFileName**

- Diğer şablon özellikleri

> [!NOTE]
> Günlüğe kaydetmeyi devre dışı bırakmak için pkgdef dosyasını kaldırın veya değerini `EnableTemplateDiscoveryLog` olarak değiştirin `dword:00000000` ve sonra `devenv /updateConfiguration` yeniden çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel proje ve öğe şablonları oluşturma](creating-custom-project-and-item-templates.md)
- [Visual Studio sorunlarını giderme](/troubleshoot/visualstudio/welcome-visual-studio/)
