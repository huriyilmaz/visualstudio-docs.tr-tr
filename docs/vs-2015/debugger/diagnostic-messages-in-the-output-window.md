---
title: Çıkış Penceresi tanılama Iletileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.output
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 60f8da2430e1c84af3c26be31c6de561291c8c6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695291"
---
# <a name="diagnostic-messages-in-the-output-window"></a>Çıkış Penceresindeki Tanılama İletileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çalışma zamanı iletilerini çıkış penceresine, sınıf kitaplığının bir parçası olan Debug sınıfını veya Trace sınıfını kullanarak yazabilirsiniz <xref:System.Diagnostics> . Yalnızca programınızın hata ayıklama sürümüne çıktıdıysanız Debug sınıfını kullanın. Hata ayıklama ve sürüm sürümlerinde çıkış istiyorsanız Trace sınıfını kullanın.  
  
## <a name="output-methods"></a>Çıkış yöntemleri  
 <xref:System.Diagnostics.Trace>Ve <xref:System.Diagnostics.Debug> sınıfları aşağıdaki çıkış yöntemlerini sağlar:  
  
- Farklı `Write` Yöntemler, önemli bir yürütme olmadan bilgi çıktı. Bu yöntemler `Debug.Print` Visual Basic önceki sürümlerinde kullanılan yöntemi değiştirir.  
  
- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> ve <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> belirli bir koşul başarısız olursa yürütme ve çıkış bilgilerini kesen Yöntemler. Varsayılan olarak, `Assert` yöntemi bilgileri bir iletişim kutusunda görüntüler. Daha fazla bilgi için bkz. [Yönetilen koddaki Onaylamalar](../debugger/assertions-in-managed-code.md).  
  
- <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName>Hem <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> yürütme hem de çıkış bilgilerini her zaman kesen ve yöntemleri. Varsayılan olarak, `Fail` Yöntemler bilgileri bir iletişim kutusunda görüntüler.  
  
  Uygulamadan gelen programa ek olarak, **Çıkış** penceresinde hakkındaki bilgiler görüntülenebilir:  
  
- Hata ayıklayıcı tarafından yüklenen veya yüklenmeyen modüller.  
  
- Oluşturulan özel durumlar.  
  
- Çıkış işlemi.  
  
- Çıkış yapan iş parçacıkları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)   
 [Çıkış Penceresi](../ide/reference/output-window.md)   
 [Uygulamaları izleme ve Işaretleme](https://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)   
 [Izleme ve Izlemeye giriş](https://msdn.microsoft.com/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)   
 [C#, F # ve Visual Basic proje türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
