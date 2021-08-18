---
title: Windows hizmetlerinde hata ayıklamaya hazırlanma | Microsoft Docs
description: Visual Studio Windows altında arka planda çalışan programlar olan Windows hizmetlerinde hata ayıklamaya hazırlanın.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3b1a83c5343b185780556ff3a7132d1d7a1a5baa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122113058"
---
# <a name="debugging-preparation-windows-services"></a>Hata Ayıklama Hazırlığı: Windows Hizmetleri
Windows hizmeti, Microsoft Windows altında arka planda çalışan bir programdır. bu örnek, bilgisayarınızın görünür saatini güncelleştiren Telnet hizmetini ve Windows saat hizmetini içerir. Windows bir hizmet içinden çalıştırılamaz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ; hizmet denetimi yöneticisi 'nin bağlamı içinde çalıştırılmalıdır. daha fazla bilgi için bkz. [Windows hizmetleri oluşturma](/dotnet/framework/windows-services/how-to-create-windows-services), [hizmet uygulamalarında hata ayıklama Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)ve [hizmet uygulamaları Windows](/dotnet/framework/windows-services/index).

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [C#, F# ve Visual Basic Proje Türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [C# hata ayıklama yapılandırması için Project Ayarlar](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic hata ayıklama yapılandırması için Ayarlar Project](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Nasıl yapılır: OnStart yönteminde hata ayıklama](../debugger/how-to-debug-the-onstart-method.md)