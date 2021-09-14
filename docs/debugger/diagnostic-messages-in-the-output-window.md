---
title: Çıkış penceresine ileti | Microsoft Docs
description: Hata Ayıklama sınıfını veya System.Diagnostics sınıf kitaplığının bir parçası olan Trace sınıfını kullanarak çalışma zamanı iletilerini Visual Studio penceresindeki Çıkış penceresine yazın.
ms.custom: SEO-VS-2020
ms.date: 11/08/2018
ms.topic: how-to
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c7ec9cfa05be11cb17e5a6ed6d768e1335cf5860
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725427"
---
# <a name="send-messages-to-the-output-window"></a>Çıkış penceresine ileti gönderme

Sınıf kitaplığının parçası olan sınıfını **veya** sınıfını kullanarak Çıkış penceresine çalışma <xref:System.Diagnostics.Debug> zamanı iletileri <xref:System.Diagnostics.Trace> <xref:System.Diagnostics> yazabilirsiniz. Yalnızca <xref:System.Diagnostics.Debug> programınız için Hata Ayıklama sürümünde *çıkışa sahip olmak* için sınıfını kullanın. Hem <xref:System.Diagnostics.Trace> Hata Ayıklama hem de Yayın sürümlerinde *çıkışa sahip olmak için* *sınıfını* kullanın.

## <a name="output-methods"></a>Çıkış yöntemleri
 ve <xref:System.Diagnostics.Trace> <xref:System.Diagnostics.Debug> sınıfları aşağıdaki çıkış yöntemlerini sağlar:

- Yürütmeyi `Write` kesmeden bilgileri çıkış olarak alan çeşitli yöntemler. Bu yöntemler, önceki `Debug.Print` sürümlerde kullanılan yöntemin yerini Visual Basic.

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> ve <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> yöntemleri, belirtilen bir koşul başarısız olursa yürütmeyi ve çıktı bilgilerini bozan. Varsayılan olarak yöntemi `Assert` bilgileri bir iletişim kutusunda görüntüler. Daha fazla bilgi için [bkz. Yönetilen kodda onaylar.](../debugger/assertions-in-managed-code.md)

- Yürütme <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> ve çıkış bilgilerini her zaman <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> bozan ve yöntemleri. Varsayılan olarak, `Fail` yöntemler bilgileri bir iletişim kutusunda görüntüler.

Çıkış **penceresi** aşağıdakiler hakkında bilgi de gösterir:

- Hata ayıklayıcısının yüklemiş veya kaldırmış olduğu modüller.

- Atılan özel durumlar.

- Çıkan işlemler.

- Çıkan iş parçacıkları.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)
- [Çıktı penceresi](../ide/reference/output-window.md)
- [İzleme ve işaretleme uygulamaları](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [C#, F# ve Visual Basic türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)
