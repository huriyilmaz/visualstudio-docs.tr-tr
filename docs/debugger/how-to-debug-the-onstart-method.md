---
title: OnStart yönteminde hata ayıkla | Microsoft Docs
description: hata ayıklayıcıyı yöntemin içinden başlatarak Visual Studio bir Windows hizmetinin OnStart yönteminde hata ayıklamanın nasıl yapılacağını öğrenin.
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
ms.openlocfilehash: de3f60072ed476bf0fb9336bea741f8e6d647f0c877664c808a7adabf69f39e9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121362151"
---
# <a name="how-to-debug-the-onstart-method"></a>Nasıl Yapılır: OnStart Yönteminde Hata Ayıklama
hizmeti başlatarak ve hata ayıklayıcıyı hizmet sürecine ekleyerek bir Windows hizmetinde hata ayıklaması yapabilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: Windows hizmeti uygulamalarında hata ayıklama](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). ancak, <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> bir Windows hizmeti yönteminde hata ayıklamak için, hata ayıklayıcıyı yöntemin içinden başlatmanız gerekir.

1. Yönteminin başına öğesine bir çağrı ekleyin <xref:System.Diagnostics.Debugger.Launch%2A> `OnStart()` .

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Hizmeti başlatın ( `net start` **Hizmetler** penceresinde kullanabilir veya başlatabilirsiniz).

    Aşağıdakine benzer bir iletişim kutusu görmeniz gerekir:

    ![WindowsService-Asis.exe içinde işlenmemiş bir .NET Framework özel durumu gösteren Visual Studio tam zamanında hata ayıklayıcı iletişim kutusunun ekran görüntüsü.](../debugger/media/onstartdebug.png)

3. **Evet, hata ayıkla ' yı seçin \<service name> .**

4. tam zamanında hata ayıklayıcı penceresinde, hata ayıklama için kullanmak istediğiniz Visual Studio sürümünü seçin.

    ![olası hata ayıklayıcılar listesinde ' yeni Microsoft Visual Studio 2015 ' örneğiyle Visual Studio tam zamanında hata ayıklayıcı penceresinin ekran görüntüsü.](../debugger/media/justintimedebugger.png)

5. Visual Studio yeni bir örneğini başlatır ve yürütme `Debugger.Launch()` yöntemde durdurulur.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
