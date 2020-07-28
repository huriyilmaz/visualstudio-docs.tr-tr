---
title: Birlikte Çalışabilirlik Uyarıları
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74bffffa2b4f95aeab20438199bb19693a1a3b94
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87235127"
---
# <a name="interoperability-warnings"></a>Birlikte Çalışabilirlik Uyarıları

Birlikte çalışabilirlik uyarıları COM istemcileriyle etkileşimi destekler.

## <a name="in-this-section"></a>Bu Bölümde

| Kural | Açıklama |
| - | - |
| [CA1400: P/Invoke giriş noktaları bulunmalıdır](../code-quality/ca1400.md) | Ortak veya korumalı yöntem System.Runtime.InteropServices.DllImportAttribute özniteliği kullanılarak işaretlenir. Yönetilmeyen kitaplık bulunamadı ya da yöntem için bir işlev kitaplığında eşleştirilemedi. |
| [CA1401: P/Invoke görünür olmamalıdır](../code-quality/ca1401.md) | Ortak bir türdeki ortak veya korumalı yöntemin System.Runtime.InteropServices.DllImportAttribute özniteliği vardır (Ayrıca, Visual Basic Declare anahtar sözcüğü tarafından uygulanır). Bu tür yöntemler açıkta kalmamalıdır. |
| [CA1402: COM görünebilir arabirimler içinde aşırı yüklemelerden kaçının](../code-quality/ca1402.md) | Aşırı yüklenmiş yöntemler COM istemcilerine maruz kaldığında, sadece ilk yöntem aşırı yüklemesi adını korur. Sonraki aşırı yüklemeler adının sonuna alt çizgi karakteri (_) eklenerek ve aşırı yüklemenin tanımını karşılayacak şekilde bir tam sayı eklenerek benzersiz olarak yeniden adlandırılır. |
| [CA1403: Otomatik yerleşim türleri COM görünebilir olmamalıdır](../code-quality/ca1403.md) | COM görünebilir bir değer türü, LayoutKind. Auto olarak ayarlanan System. Runtime. InteropServices. StructLayoutAttribute özniteliği kullanılarak işaretlenir. Bu türlerin düzeni .NET sürümleri arasında değişebilir ve bu, belirli bir düzeni bekleyen COM istemcilerini keser. |
| [CA1404: P/Invoke sonrasında GetLastError çağrısı yapın](../code-quality/ca1404.md) | Marshal. GetLastWin32Error yöntemine veya denk GetLastError işlevine bir çağrı yapılır [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] ve hemen önceki çağrı bir platform çağırma yöntemine değildir. |
| [CA1405: COM görünebilir tür taban türler COM görünebilir olmalıdır](../code-quality/ca1405.md) | COM görünür türü, görünmeyen bir COM türünden türer. |
| [CA1406: Visual Basic 6 istemcileri için Int64 bağımsız değişkenlerinden kaçının](../code-quality/ca1406.md) | Visual Basic 6 COM istemcisi 64-bit tamsayıya erişemez. |
| [CA1407: COM görünebilir türler içinde statik üyelerden kaçının](../code-quality/ca1407.md) | COM statik yöntemleri desteklemez. |
| [CA1408: AutoDual ClassInterFaceType kullanmayın](../code-quality/ca1408.md) | Çift arabirim kullanan türler, belirli bir arabirim düzenine bağlanmak için istemcileri etkinleştirir. Gelecek sürümdeki değişiklikler, türün düzeni veya bazı temel türler, arayüze bağlanan COM istemcilerini kesintiye uğratır. Varsayılan olarak, ClassInterfaceAttribute özniteliği belirtilmezse, salt dağıtılan arabirim kullanılır. |
| [CA1409: COM görünebilir türler oluşturulabilir olmalıdır](../code-quality/ca1409.md) | Özellikle COM görünür olarak işaretlenmiş bir başvuru türü, parametreli ortak kurucu içeriyorsa ancak genel varsayılan (parametresiz) bir oluşturucuya sahip değildir. Genel varsayılan oluşturucu olmadan tür COM istemcileri tarafından oluşturulmamalıdır. |
| [CA1410: COM kayıt metotları eşleşmelidir](../code-quality/ca1410.md) | Bir tür, özniteliği kullanılarak işaretlenen, <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ancak özniteliği kullanılarak işaretlenmiş bir yöntemi bildirmeyen bir yöntemi bildirir <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> veya tam tersi de geçerlidir. |
| [CA1411: COM kayıt metotları görünebilir olmamalıdır](../code-quality/ca1411.md) | System. Runtime. InteropServices. ComRegisterFunctionAttribute özniteliği veya System. Runtime. InteropServices. ComUnregisterFunctionAttribute özniteliği kullanılarak işaretlenen bir yöntem dışarıdan görünür. |
| [CA1412: ComSource arabirimlerini IDispatch olarak işaretleyin](../code-quality/ca1412.md) | System.Runtime.InteropServices.ComSourceInterfacesAttribute özniteliğini kullanarak işaretlenen bir tür ve belirtilen arabirimlerden birini ayarlamak için ComInterfaceType.InterfaceIsIDispatch özniteliğine System.Runtime.InteropServices.InterfaceTypeAttribute özniteliğini kullanarak ayarlanır. |
| [CA1413: COM görünebilir değer türleri içinde genel olmayan alanlardan kaçının](../code-quality/ca1413.md) | COM-görünür değer türlerinin ortak olmayan örnek alanları COM istemcilerine görünürdür. Maruz kalmaması gereken, istenmeyen bir tasarım ya da güvenlik etkileri olan bilgi alanındaki içeriği gözden geçirin. |
| [CA1414: Boolean P/Invoke bağımsız değişkenlerini MarshalAs ile Işaretleyin](../code-quality/ca1414.md) | Boolean veri türünün, yönetimsiz kod içinde birden fazla sunumu vardır. |
| [CA1415: P/Invoke doğru olarak bildir](../code-quality/ca1415.md) | Bu kural, ÇAKıŞAN bir yapı parametresine işaretçi olan işlevleri hedefleyen platform çağırma yöntemi bildirimlerini arar [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] ve karşılık gelen yönetilen parametre bir yapıya işaretçi değildir <xref:System.Threading.NativeOverlapped?displayProperty=fullName> . |
| [CA1417: `OutAttribute` P/Invoke için dize parametrelerinde kullanmayın](../code-quality/ca1417.md) | Değeri ile geçirilen dize parametreleri, `OutAttribute` dize birbirine bağlı bir dizeyse çalışma zamanının kararlılığını bozabilir. |