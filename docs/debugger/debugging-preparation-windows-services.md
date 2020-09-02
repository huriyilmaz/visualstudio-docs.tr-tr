---
title: Windows hizmetlerinde hata ayıklamaya hazırlanma | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3161f6d2c328e8e33dd82ed206aa8aa20e654cc9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72738084"
---
# <a name="debugging-preparation-windows-services"></a>Hata Ayıklama Hazırlığı: Windows Hizmetleri
Windows hizmeti, Microsoft Windows altında arka planda çalışan bir programdır. Bu örnek, bilgisayarınızın görünür saatini güncelleştiren Telnet hizmetini ve Windows Saat hizmetini içerir. Bir Windows hizmeti içinden çalıştırılamaz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ; hizmet denetimi Yöneticisi 'nin bağlamı içinde çalıştırılmalıdır. Daha fazla bilgi için bkz. [Windows Hizmetleri oluşturma](/dotnet/framework/windows-services/how-to-create-windows-services), [Windows hizmet uygulamalarında hata ayıklama](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)ve [Windows hizmet uygulamaları](/dotnet/framework/windows-services/index).

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [C#, F# ve Visual Basic Proje Türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [C# Hata Ayıklama Yapılandırması Proje Ayarları](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic Hata Ayıklama Yapılandırması Proje Ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Nasıl yapılır: OnStart yönteminde hata ayıklama](../debugger/how-to-debug-the-onstart-method.md)