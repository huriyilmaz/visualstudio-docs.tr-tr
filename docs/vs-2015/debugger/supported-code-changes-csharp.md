---
title: Desteklenen kod değişiklikleri (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fc02c11a4ebceea431fc06a1bd1cfdb1063097d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67823531"
---
# <a name="supported-code-changes-c"></a>Desteklenen Kod Değişiklikleri (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenle ve devam et, yöntem gövdelerinde birçok kod değişikliği türünü işler. Ancak Yöntem gövdelerinin dışındaki değişiklikler ve Yöntem gövdelerinin içindeki birkaç değişiklik, hata ayıklama sırasında uygulanamaz. Bu desteklenmeyen değişiklikleri uygulamak için, hata ayıklamayı durdurmanız ve kodun yeni bir sürümüyle yeniden başlatmanız gerekir.  
  
 Hata ayıklama oturumu sırasında C# koduna aşağıdaki değişiklikler uygulanamaz:  
  
- Geçerli ifadede veya diğer etkin deyimdeki değişiklikler.  
  
     Etkin deyimler, geçerli ifadeye ulaşmak için çağrılan çağrı yığınında işlevlerde tüm deyimleri içerir.  
  
     Geçerli ifade, kaynak pencerede sarı bir arka plan ile işaretlendi. Diğer etkin deyimler gölgeli bir arka plan ile işaretlenir ve salt okunurdur. Bu varsayılan renkler **Seçenekler** iletişim kutusunda değiştirilebilir.  
  
- Bir türün imzasını değiştirme.  
  
- Daha önce yakalanamayan bir değişkeni yakalayan anonim bir yöntem ekleme.  
  
- Öznitelikleri ekleme, kaldırma veya değiştirme.  
  
- Yönergeler ekleme, kaldırma veya değiştirme `using` .  
  
- `foreach` `using` `lock` Etkin deyimin etrafına, veya çevresine ekleniyor.  
  
## <a name="unsafe-code"></a>Güvenli olmayan kod  
 Güvenli olmayan koddaki değişiklikler, güvenli koddaki değişikliklerle aynı sınırlamalara sahiptir ve bir ek kısıtlamadır: Düzenle ve devam et işleci içeren bir yöntem içinde çıkış olmayan güvenli olmayan koddaki değişiklikleri desteklemez `stackalloc` .  
  
## <a name="exceptions"></a>Özel durumlar  
 Düzenle ve devam et `catch` `finally` , `catch` `finally` etkin deyimin etrafında bir veya blok eklenmesine izin verilmediğinden, ve bloklara yapılan değişiklikleri destekler.  
  
## <a name="unsupported-scenarios"></a>Desteklenmeyen Senaryolar  
 Düzenle ve devam et aşağıdaki hata ayıklama senaryolarında kullanılamaz:  
  
- Bazı durumlarda LINQ kodunda hata ayıklama. Daha fazla bilgi için bkz. [LINQ hata ayıklama](../debugger/debugging-linq.md).  
  
  - Daha önce yakalanamayan bir değişken yakalama.  

  - Sorgu ifadesinin türü değiştiriliyor (örn. bir = seçin> yeni {A = a} seçin;)  

  - Etkin bir `where` ifade içeren bir öğesini kaldırma.  

  - Etkin bir `let` ifade içeren bir öğesini kaldırma.  

  - Etkin bir `join` ifade içeren bir öğesini kaldırma.  

  - Etkin bir `orderby` ifade içeren bir öğesini kaldırma.  
  
- Karışık mod (Yerel/yönetilen) hata ayıklama.  
  
- SQL hata ayıklaması.  
  
- Dr. Watson dökümünü hata ayıklama.  
  
- İşlenmemiş bir özel durumdan sonra kodu düzenlemeyle, "**işlenmemiş özel durumlarla çağrı yığınını geriye doğru izleme**" seçeneği seçili değildir.  
  
- Gömülü çalışma zamanı uygulamasında hata ayıklama.  
  
- **Hata ayıklama** menüsünden **başla** ' yı seçerek uygulamayı çalıştırmak yerine **öğesine** eklenen bir uygulamada hata ayıklama.  
  
- İyileştirilmiş kodda hata ayıklama.  
  
- Derleme hataları nedeniyle yeni bir sürüm derlenemedi sonra kodunuzun eski bir sürümünde hata ayıklama işlemi başarısız oldu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Düzenle ve devam et (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Nasıl Yapılır: Düzenle ve Devam Et'i Kullanma (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)
