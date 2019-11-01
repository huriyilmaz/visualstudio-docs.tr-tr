---
title: Düzenle ve devam et hata iletisi iletişim kutusu | Microsoft Docs
ms.date: 10/15/2018
ms.topic: reference
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7df95eae689f7c3abbb0d75a7557ce749bdceee5
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188229"
---
# <a name="edit-and-continue-error-message"></a>Düzenle ve devam et hata iletisi

Düzenle ve devam et 'i destekleyen bir kod dilinde hata ayıklaması yaparken **Düzenle ve devam et** hata iletisi kutusu görüntülenir, ancak yaptığınız kod değişiklikleri için Düzenle ve devam et kullanılamaz. Hata mesajı daha ayrıntılı bir açıklama sağlar. İletişim kutusunu yanıtlamak için, iletişim kutusunu kapatmak için **Tamam** ' ı seçin ve düzenleme girişimini iptal edin.

Bu hata iletisinin olası nedenleri şunlardır:

- SQL Server kodu düzenlenmeye çalışılıyor.
- En iyileştirilmiş kod düzenlenmeye çalışılıyor. Bir yayın derlemeden bir hata ayıklama derlemesine geçmeniz gerekebilir.
- Hata ayıklayıcıda duraklalarken, çalışırken kodu düzenlemeye çalışılıyor. [Kesme noktası ayarlamayı](../debugger/using-breakpoints.md)ve duraklalarken kodu düzenlemenizi deneyin.
- Yalnızca yönetilmeyen hata ayıklama etkinleştirildiğinde yönetilen kodu düzenlemeye çalışılıyor. Düzenle ve devam et [karışık modda hata ayıklama](../debugger/how-to-debug-in-mixed-mode.md)ile çalışmaz.
- Programlama dilinizde Düzenle ve devam et tarafından desteklenmeyen bir kod değişikliği yapılıyor. Daha fazla bilgi için, [içinde C#desteklenen kod değişiklikleri ](supported-code-changes-csharp.md), [Visual Basic Düzenle ve devam et ' de desteklenmeyen düzenlemeler](supported-code-changes-csharp.md)ve [desteklenen C++ kod değişiklikleri](supported-code-changes-cpp.md)hakkındaki makalelere bakın.
- **Hata** ayıklama menüsünden hata ayıklama başlatmak yerine, bağlı olduğunuz bir uygulamadaki kodu düzenlemeye çalışılıyor.
- Dr. Watson dökümünden hata ayıklarken kodu düzenlemeye çalışılıyor.
- İşlenmeyen bir özel durum oluştuktan sonra kodu düzenlemeye çalışılıyor ve **işlenmemiş özel durumlarla çağrı yığınını bırakma** seçeneği seçili değil.
- Gömülü çalışma zamanı uygulamasında hata ayıklarken kodu düzenlemeye çalışılıyor.
- 64 bit uygulama hedefi ile 4.5.1 'ten önceki bir .NET Framework sürümünü kullanarak yönetilen kodu düzenlemeye çalışılıyor. 4\.5.1 ' den önceki .NET Framework Düzenle ve devam et özelliğini kullanmak için, **\<ProjectName >**  > **Özellikler** > **derleme** sekmesi, **Gelişmiş derleyici** ayarında hedefi **x86** olarak ayarlayın.
- Hata ayıklama sırasında değiştirilmiş ve yeniden yüklenmiş bir derlemede kod düzenlemeye çalışılıyor.
- Yüklenemeyen bir derlemede kod düzenlemeye çalışılıyor.
- En son sürümde derleme hataları olduğundan, uygulamanın eski bir sürümünde hata ayıklama işlemi başlatılıyor.

Daha fazla bilgi için bkz.:
- [C++Düzenle ve devam et blog gönderisi](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [Desteklenen kod değişiklikleri (C++)](../debugger/supported-code-changes-cpp.md)
- [Düzenle ve Devam Et](../debugger/edit-and-continue.md)