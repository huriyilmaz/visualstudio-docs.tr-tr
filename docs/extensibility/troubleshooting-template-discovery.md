---
title: Visual Studio 'da şablon bulma sorunlarını giderme | Microsoft Docs
ms.date: 01/02/2018
ms.topic: troubleshooting
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89ff5b9974f20841378f367c3cb631a8d4cf7787
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87235049"
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

3. Yüklemeniz için bir [Geliştirici komut istemi](/dotnet/framework/tools/developer-command-prompt-for-vs) açın ve çalıştırın `devenv /updateConfiguration` .

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
