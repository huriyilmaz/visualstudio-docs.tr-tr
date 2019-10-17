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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0380f57a5e138cf9189322fc27820cbb838e5b50
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72445821"
---
# <a name="interoperability-warnings"></a>Birlikte Çalışabilirlik Uyarıları

Birlikte çalışabilirlik uyarıları COM istemcileriyle etkileşimi destekler.

## <a name="in-this-section"></a>Bu Bölümde

| Kural | Açıklama |
| - | - |
| [CA1400: P/Invoke giriş noktaları bulunmalıdır](../code-quality/ca1400-p-invoke-entry-points-should-exist.md) | Ortak veya korumalı yöntem System.Runtime.InteropServices.DllImportAttribute özniteliği kullanılarak işaretlenir. Yönetilmeyen kitaplık bulunamadı ya da yöntem için bir işlev kitaplığında eşleştirilemedi. |
| [CA1401: P/Invoke'lar görünür olmamalıdır](../code-quality/ca1401-p-invokes-should-not-be-visible.md) | Ortak türde ortak veya korumalı bir yöntem System. Runtime. InteropServices. DllImportAttribute özniteliğine sahiptir (Ayrıca, Visual Basic içinde Declare anahtar sözcüğü tarafından uygulanır). Bu tür yöntemler açıkta kalmamalıdır. |
| [CA1402: COM görünebilir arabirimler içinde aşırı yüklemelerden kaçının](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md) | Aşırı yüklenmiş yöntemler COM istemcilerine maruz kaldığında, sadece ilk yöntem aşırı yüklemesi adını korur. Sonraki aşırı yüklemeler adının sonuna alt çizgi karakteri (_) eklenerek ve aşırı yüklemenin tanımını karşılayacak şekilde bir tam sayı eklenerek benzersiz olarak yeniden adlandırılır. |
| [CA1403: Otomatik yerleşim türleri COM görünebilir olmamalıdır](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md) | COM görünebilir bir değer türü, LayoutKind. Auto olarak ayarlanan System. Runtime. InteropServices. StructLayoutAttribute özniteliği kullanılarak işaretlenir. Bu türlerin düzeni .NET sürümleri arasında değişebilir ve bu, belirli bir düzeni bekleyen COM istemcilerini keser. |
| [CA1404: P/Invoke ardından hemen GetLastError çağırın](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md) | Marshal. GetLastWin32Error yöntemine veya eşdeğer [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] GetLastError işlevine bir çağrı yapılır ve hemen önceki çağrı bir platform çağırma yöntemine değildir. |
| [CA1405: COM görünebilir tür taban türler COM görünebilir olmalıdır](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md) | COM görünür türü, görünmeyen bir COM türünden türer. |
| [CA1406: Visual Basic 6 istemcileri için Int64 bağımsız değişkenlerinden kaçının](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md) | Visual Basic 6 COM istemcisi 64-bit tamsayıya erişemez. |
| [CA1407: COM görünebilir türler içinde statik üyelerden kaçının](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md) | COM statik yöntemleri desteklemez. |
| [CA1408: AutoDual ClassInterfaceType kullanma](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md) | Çift arabirim kullanan türler, belirli bir arabirim düzenine bağlanmak için istemcileri etkinleştirir. Gelecek sürümdeki değişiklikler, türün düzeni veya bazı temel türler, arayüze bağlanan COM istemcilerini kesintiye uğratır. Varsayılan olarak, ClassInterfaceAttribute özniteliği belirtilmezse, salt dağıtılan arabirim kullanılır. |
| [CA1409: Com görünebilir türler oluşturulabilmelidir](../code-quality/ca1409-com-visible-types-should-be-creatable.md) | Özellikle COM görünür olarak işaretlenmiş bir başvuru türü, parametreli ortak kurucu içeriyorsa ancak genel varsayılan (parametresiz) bir oluşturucuya sahip değildir. Genel varsayılan oluşturucu olmadan tür COM istemcileri tarafından oluşturulmamalıdır. |
| [CA1410: COM kayıt yöntemleri eşleşmelidir](../code-quality/ca1410-com-registration-methods-should-be-matched.md) | Bir tür, <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> özniteliği kullanılarak işaretlenen, ancak <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> özniteliği kullanılarak işaretlenmiş bir yöntemi bildirmeyen veya tam tersi bir yöntem bildirir. |
| [CA1411: COM kayıt yöntemleri görünebilir olmamalıdır](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md) | System. Runtime. InteropServices. ComRegisterFunctionAttribute özniteliği veya System. Runtime. InteropServices. ComUnregisterFunctionAttribute özniteliği kullanılarak işaretlenen bir yöntem dışarıdan görünür. |
| [CA1412: ComSource Arabirimlerini IDispatch olarak işaretleyin](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md) | System.Runtime.InteropServices.ComSourceInterfacesAttribute özniteliğini kullanarak işaretlenen bir tür ve belirtilen arabirimlerden birini ayarlamak için ComInterfaceType.InterfaceIsIDispatch özniteliğine System.Runtime.InteropServices.InterfaceTypeAttribute özniteliğini kullanarak ayarlanır. |
| [CA1413: COM görünebilir değer türleri içinde genel olmayan alanlardan kaçının](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | COM-görünür değer türlerinin ortak olmayan örnek alanları COM istemcilerine görünürdür. Maruz kalmaması gereken, istenmeyen bir tasarım ya da güvenlik etkileri olan bilgi alanındaki içeriği gözden geçirin. |
| [CA1414: Boolean P/Invoke bağımsız değişkenlerini MarshalAs ile işaretleyin](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | Boolean veri türünün, yönetimsiz kod içinde birden fazla sunumu vardır. |
| [CA1415: P/Invoke'ları doğru bildirin](../code-quality/ca1415-declare-p-invokes-correctly.md) | Bu kural, ÇAKıŞAN bir yapı parametresine işaretçi olan [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] işlevlerini hedefleyen platform çağırma yöntemi bildirimlerine bakar ve karşılık gelen yönetilen parametre <xref:System.Threading.NativeOverlapped?displayProperty=fullName> yapısına yönelik bir işaretçi değildir. |
