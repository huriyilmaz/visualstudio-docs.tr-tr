---
title: Desteklenen Kod Değişiklikleri (C# ve Visual Basic) | Microsoft Docs
description: Bir C# veya Visual Basic projesinde hata ayıklarken Düzenle ve Devam Bırak özelliğini kullanırken hangi kod Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 9/03/2020
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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 4f51cc979f968acf0cf1fb526d88c86a8fc09ad4
ms.sourcegitcommit: 2430a38f23ac17b65dd8d3baa806e90433aba24f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2021
ms.locfileid: "115094259"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Desteklenen kod değişiklikleri (C# ve Visual Basic)
Düzenle ve Devam Etmek, yöntem gövdeleri içindeki çoğu kod değişikliği türlerini işlemeye devam eder. Ancak çoğu yöntem gövdeleri dışındaki değişiklikler ve yöntem gövdeleri içindeki birkaç değişiklik, hata ayıklama sırasında uygulanamaz. Bu desteklenmeyen değişiklikleri uygulamak için hata ayıklamayı durdurmanız ve kodun yeni bir sürümüyle yeniden başlatmanız gerekir.

## <a name="supported-changes-to-code"></a>Kodda desteklenen değişiklikler

Aşağıdaki tabloda, oturum yeniden başlatılmadan hata ayıklama oturumu sırasında C# Visual Basic kodda yapılan değişiklikler gösterilmiştir.

|Dil öğesi/özellik|Desteklenen düzenleme işlemi|Sınırlamalar|
|-|-|-|
|Türler|Yöntemleri, alanları, oluşturucuları ve diğer yöntemleri ekleme|[Evet](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Yineleyiciler|Ekleme veya değiştirme|No|
|async/await ifadeleri|Ekleme veya değiştirme|[Evet](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Dinamik nesneler|Ekleme veya değiştirme|No|
|lambda ifadeleri|Ekleme veya değiştirme|[Evet](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|LINQ ifadeleri|Ekleme veya değiştirme|[Lambda ifadeleri ile aynı](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|

> [!NOTE]
> Dize ilişkilendirme ve null koşullu işleçler gibi daha yeni dil özellikleri genellikle Düzenle ve Devam Ile de desteklene. En güncel bilgiler için [Enc Desteklenen Düzenlemeler sayfasına](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md) bakın.

## <a name="unsupported-changes-to-code"></a>Kodda desteklenmeyen değişiklikler
 Hata ayıklama oturumu sırasında C# ve Visual Basic aşağıdaki değişiklikler uygulanamaz:

- Geçerli deyimde veya başka bir etkin deyimde yapılan değişiklikler.

     Etkin deyimler, çağrı yığınındaki işlevlerde geçerli deyime almak için çağrılan deyimleri içerir.

     Geçerli deyim, kaynak pencerede sarı bir arka plan ile işaretlenir. Diğer etkin deyimler gölgeli bir arka plan ile işaretlenir ve salt okunur olur. Bu varsayılan renkler Seçenekler iletişim **kutusunda değiştirilebilir.**

- Aşağıdaki tabloda dil öğesine göre kodda desteklenmeyen değişiklikler yer alır.

|Dil öğesi/özellik|Desteklenmeyen düzenleme işlemi|
|-|-|
|Tüm kod öğeleri|Yeni -den adlandırma|
|Ad alanları|Ekle|
|Ad alanları, türler, üyeler|Sil|
|Genel Türler|Ekleme veya değiştirme|
|Arabirimler|Değiştir|
|Türler|Soyut veya sanal üye ekleme, geçersiz kılma ekleme [(ayrıntılara bakın)](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Türler|Yok etme ekleme|
|Üyeler|Katıştırılmış birlikte çalışma türüne başvuran bir üyeyi değiştirme|
|Üyeler|Kod yürüterek statik üyeye zaten erişildikten sonra bu üyeyi değiştirme|
|Üyeler (Visual Basic)|On Error veya Resume deyimiyle üyeyi değiştirme|
|Üyeler (Visual Basic)|Toplama, GrupLama, Basit Birleştirme veya Grup Birleştirme LINQ sorgu yan tümcesi içeren bir üyeyi değiştirme|
|Yöntemler|İmzaları değiştirme|
|Yöntemler|Bir yöntem gövdesi ekleyerek soyut yöntemi soyut olmayan bir yöntem haline|
|Yöntemler|Delete yöntemi gövdesi|
|Öznitelikler|Ekleme veya değiştirme|
|Olaylar veya özellikler|Tür parametresini, temel türü, temsilci türünü veya dönüş türünü değiştirme |
|İşleçler veya dizinciler|Tür parametresini, temel türü, temsilci türünü veya dönüş türünü değiştirme |
|catch blokları|Etkin deyimi içerdiğinde değiştirme|
|try-catch-finally blokları|Etkin deyimi içerdiğinde değiştirme|
|using deyimleri|Ekle|
|zaman uyumsuz yöntemler/lambdalar|4 ve daha düşük bir projeyi hedeflemek için zaman uyumsuz .NET Framework/lambda değiştirme [(ayrıntılara bakın)](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|
|Yineleyiciler|4 ve daha düşük bir projeyi .NET Framework bir tekrarlayıcıyı değiştirme [(ayrıntılara bakın)](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)|

## <a name="unsafe-code"></a>Güvenli olmayan kod
 Güvenli olmayan kodda yapılan değişiklikler, güvenli kodda yapılan değişikliklerle aynı sınırlamalara sahiptir ve bir ek kısıtlama daha vardır: Düzenle ve Devam Etmek, işleci içeren bir yöntemde çıkan güvenli olmayan kodda yapılan değişiklikleri `stackalloc` desteklemez.

## <a name="unsupported-app-scenarios"></a>Desteklenmeyen uygulama senaryoları

Desteklenmeyen uygulamalar ve platformlar arasında ASP.NET 5, Silverlight 5 ve Windows 8.1.

> [!NOTE]
> Desteklenen uygulamalar arasında Windows 10'de UWP ve .NET Framework 4.6 masaüstü veya sonraki sürümleri (.NET Framework yalnızca masaüstü sürümüdür) hedef alan x86 ve x64 uygulamaları yer alır.

## <a name="unsupported-scenarios"></a>Desteklenmeyen senaryolar
 Düzenle ve Devam Bırak, aşağıdaki hata ayıklama senaryolarında kullanılamaz:

- Karma mod (yerel/yönetilen) hata ayıklama.

- SQL hata ayıklama.

- Dr. Watson dökümde hata ayıklama.

- Katıştırılmış çalışma zamanı uygulamasında hata ayıklama.

- Hata Ayıklama menüsünden Başlat'ı seçerek **uygulamayı çalıştırma yerine işleme ekleme**(  İşleme > hata ayıklama ) kullanarak uygulamada **hata** ayıklama.

- İyileştirilmiş kodda hata ayıklama.

- Derleme hataları nedeniyle yeni bir sürüm derleme başarısız olduktan sonra kodunuzun eski bir sürümünde hata ayıklama.

## <a name="see-also"></a>Ayrıca bkz.
- [Düzenle ve Devam Et (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [Nasıl Yapılır: Düzenle ve Devam Et'i Kullanma (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)