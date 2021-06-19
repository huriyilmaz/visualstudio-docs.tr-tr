---
title: Windows hizmetlerinde hata ayıklamaya hazırlanma | Microsoft Docs
description: Visual Studio 'da Windows 'un altında arka planda çalışan programlar olan Windows hizmetlerinde hata ayıklamayı hazırlayın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 01448fcd477f5b17b78ad2b142b965f30798746b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387745"
---
# <a name="debugging-preparation-windows-services"></a>Hata Ayıklama Hazırlığı: Windows Hizmetleri
Windows hizmeti, Microsoft Windows altında arka planda çalışan bir programdır. Bu örnek, bilgisayarınızın görünür saatini güncelleştiren Telnet hizmetini ve Windows Saat hizmetini içerir. Bir Windows hizmeti içinden çalıştırılamaz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ; hizmet denetimi Yöneticisi 'nin bağlamı içinde çalıştırılmalıdır. Daha fazla bilgi için bkz. [Windows Hizmetleri oluşturma](/dotnet/framework/windows-services/how-to-create-windows-services), [Windows hizmet uygulamalarında hata ayıklama](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)ve [Windows hizmet uygulamaları](/dotnet/framework/windows-services/index).

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [C#, F# ve Visual Basic Proje Türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [C# hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Nasıl yapılır: OnStart yönteminde hata ayıklama](../debugger/how-to-debug-the-onstart-method.md)