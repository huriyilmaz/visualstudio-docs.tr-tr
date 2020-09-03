---
title: Desteklenen kod değişiklikleri (C# ve Visual Basic) | Microsoft Docs
ms.date: 10/11/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
- Edit and Continue [Visual Basic], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 44881035da14483c3ddf1f4c48cb3957a1ce8b50
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72729085"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Desteklenen kod değişiklikleri (C# ve Visual Basic)
Düzenle ve devam et, yöntem gövdelerinde birçok kod değişikliği türünü işler. Ancak Yöntem gövdelerinin dışındaki değişiklikler ve Yöntem gövdelerinin içindeki birkaç değişiklik, hata ayıklama sırasında uygulanamaz. Bu desteklenmeyen değişiklikleri uygulamak için, hata ayıklamayı durdurmanız ve kodun yeni bir sürümüyle yeniden başlatmanız gerekir.

## <a name="supported-changes-to-code"></a>Koddaki desteklenen değişiklikler

Aşağıdaki tabloda, oturum yeniden başlatmadan hata ayıklama oturumu sırasında C# ve Visual Basic koduna yapılabilecek değişiklikler gösterilmektedir.

|Dil öğesi/özelliği|Desteklenen düzenleme işlemi|Sınırlamalar|
|-|-|-|
|Türler|Yöntemler, alanlar, oluşturucular, et al|[Evet](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Yineleyiciler|Ekleme veya değiştirme|Hayır|
|zaman uyumsuz/await ifadeleri|Ekleme veya değiştirme|[Evet](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Dinamik nesneler|Ekleme veya değiştirme|Hayır|
|lambda ifadeleri|Ekleme veya değiştirme|[Evet](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|LINQ ifadeleri|Ekleme veya değiştirme|[Lambda ifadeleriyle aynı](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> Dize ilişkilendirme ve null koşullu işleçler gibi daha yeni dil özellikleri genellikle Düzenle ve devam et tarafından desteklenir. En güncel bilgiler için, bkz. [ENC tarafından desteklenen düzenlemeler](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) sayfası.

## <a name="unsupported-changes-to-code"></a>Koddaki desteklenmeyen değişiklikler
 Bir hata ayıklama oturumu sırasında C# ve Visual Basic koduna aşağıdaki değişiklikler uygulanamaz:

- Geçerli ifadede veya diğer etkin deyimdeki değişiklikler.

     Etkin deyimler, geçerli ifadeye ulaşmak için çağrılan çağrı yığınında işlevlerde tüm deyimleri içerir.

     Geçerli ifade, kaynak pencerede sarı bir arka plan ile işaretlendi. Diğer etkin deyimler gölgeli bir arka plan ile işaretlenir ve salt okunurdur. Bu varsayılan renkler **Seçenekler** iletişim kutusunda değiştirilebilir.

- Aşağıdaki tabloda, dil öğesine göre koddaki desteklenmeyen değişiklikler gösterilmektedir.

|Dil öğesi/özelliği|Desteklenmeyen düzenleme işlemi|
|-|-|
|Tüm kod öğeleri|Adlandırıl|
|Ad alanları|Ekle|
|Ad alanları, türler, Üyeler|Sil|
|Genel Türler|Ekleme veya değiştirme|
|Arabirimler|Değiştir|
|Türler|Soyut veya sanal üye ekleyin, geçersiz kılma ekleyin ( [ayrıntılara](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)bakın)|
|Türler|Yıkıcı Ekle|
|Üyeler|Katıştırılmış birlikte çalışma türüne başvuran bir üyeyi değiştirme|
|Üyeler|Kod yürütülerek bir statik üyeyi zaten erişildikten sonra değiştirme|
|Üyeler (Visual Basic)|Bir üyeyi hata veya yeniden başlatma bildirimiyle değiştirme|
|Üyeler (Visual Basic)|Toplama, gruplama ölçütü, basit birleştirme veya grup birleştirme LINQ sorgu yan tümcesini içeren bir üyeyi değiştirme|
|Yöntemler|İmzaları değiştirme|
|Yöntemler|Bir soyut yöntemin bir yöntem gövdesi ekleyerek Özet olmayan hale gelmesini sağlama|
|Yöntemler|Yöntem gövdesini Sil|
|Öznitelikler|Ekleme veya değiştirme|
|Olaylar veya Özellikler|Bir tür parametresi, temel tür, temsilci türü veya dönüş türü değiştirme |
|İşleçler veya Dizin oluşturucular|Bir tür parametresi, temel tür, temsilci türü veya dönüş türü değiştirme |
|catch blokları|Etkin bir ekstre içerdiğinde Değiştir|
|try-catch-finally blokları|Etkin bir ekstre içerdiğinde Değiştir|
|using deyimleri|Ekle|
|zaman uyumsuz metotlar/Lambdalar|.NET Framework 4 ve daha düşük bir projede bir zaman uyumsuz yöntem/lambda değiştirme ( [ayrıntılara](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)bakın)|
|Yineleyiciler|.NET Framework 4 ve daha düşük bir projede bir yineleyiciyi değiştirme ( [ayrıntılara](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)bakın)|

## <a name="unsafe-code"></a>Güvenli olmayan kod
 Güvenli olmayan koddaki değişiklikler, güvenli koddaki değişikliklerle aynı sınırlamalara sahiptir ve bir ek kısıtlamadır: Düzenle ve devam et işleci içeren bir yöntem içinde çıkış olmayan güvenli olmayan koddaki değişiklikleri desteklemez `stackalloc` .

## <a name="unsupported-app-scenarios"></a>Desteklenmeyen uygulama senaryoları

Desteklenmeyen uygulamalar ve platformlar şunlardır ASP.NET 5, Silverlight 5 ve Windows 8.1.

> [!NOTE]
> Desteklenen uygulamalar Windows 10 ' da UWP ve .NET Framework 4,6 masaüstü veya sonraki sürümlerini hedefleyen x86 ve x64 uygulamaları (.NET Framework yalnızca bir masaüstü sürümüdür) içerir.

## <a name="unsupported-scenarios"></a>Desteklenmeyen senaryolar
 Düzenle ve devam et aşağıdaki hata ayıklama senaryolarında kullanılamaz:

- Karışık mod (Yerel/yönetilen) hata ayıklama.

- SQL hata ayıklaması.

- Dr. Watson dökümünü hata ayıklama.

- Gömülü çalışma zamanı uygulamasında hata ayıklama.

- **Hata** ayıklama menüsünden **Başlat** ' a tıklayarak uygulamayı çalıştırmak yerine, Işleme iliştir (**hata ayıklama > işleme**) kullanarak bir uygulamada hata ayıklayın.

- İyileştirilmiş kodda hata ayıklama.

- Derleme hataları nedeniyle yeni bir sürüm derlenemedi sonra kodunuzun eski bir sürümünde hata ayıklama işlemi başarısız oldu.

## <a name="see-also"></a>Ayrıca bkz.
- [Düzenle ve Devam Et (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [Nasıl Yapılır: Düzenle ve Devam Et'i Kullanma (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)