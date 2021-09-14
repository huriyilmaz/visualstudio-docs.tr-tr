---
title: OnStart Yöntemi hata ayıklaması | Microsoft Docs
description: Visual Studio'da bir Windows hizmetinin OnStart yönteminin hata ayıklamasını öğrenmek için yönteminin içinden hata ayıklayıcıyı başlatabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 995470a5156850bf789a233b2629a41859585440
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627993"
---
# <a name="how-to-debug-the-onstart-method"></a>Nasıl Yapılır: OnStart Yönteminde Hata Ayıklama
Hizmeti başlatarak Windows hata ayıklayıcısını hizmet sürecine eklayarak bir hizmette hata ayıkabilirsiniz. Daha fazla bilgi için, [bkz. How to: Debug Windows Service Applications](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Ancak, bir Windows hizmetinin yönteminde hata <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> ayıklamak için, yönteminin içinden hata ayıklayıcıyı başlatmalı.

1. yönteminin başına <xref:System.Diagnostics.Debugger.Launch%2A> çağrısı `OnStart()` ekleyin.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Hizmeti başlatma (kullanabilir veya `net start` Hizmetler penceresinde  başlatabilirsiniz).

    Aşağıdakine benzer bir iletişim kutusu görüyor gerekir:

    ![Hata ayıklamada Visual Studio bir özel durum olduğunu gösteren Tam Zamanında Hata Ayıklayıcısı iletişim .NET Framework ekran WindowsService-Asis.exe.](../debugger/media/onstartdebug.png)

3. Evet, **hata ayıkla seçeneğini \<service name> seçin.**

4. Tam Zamanında Hata Ayıklayıcısı penceresinde, hata ayıklama için Visual Studio istediğiniz uygulamanın sürümünü seçin.

    ![Olası Hata Ayıklayıcılar Visual Studio 'Yeni Microsoft Visual Studio 2015' örneği seçilmiş tam zamanında hata ayıklayıcısı penceresinin ekran görüntüsü.](../debugger/media/justintimedebugger.png)

5. Yeni bir Visual Studio başlatılır ve yönteminde yürütme `Debugger.Launch()` durdurulur.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcı Güvenliği](../debugger/debugger-security.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
