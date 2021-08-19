---
title: Düzenle ve Devam Ediyor hata iletisi iletişim kutusu| Microsoft Docs
description: Düzenle ve Devam Etme, kod değişiklikleriniz için kullanılabilir olmadığını bildirebilirsiniz. Bu makale olası nedenler sağlar.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 28fee1e361afbd40e8ebd134dfd702beb9c2b270
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147020"
---
# <a name="edit-and-continue-error-message"></a>Düzenle ve Devam Ediyor hata iletisi

Düzenle **ve Devam** Etme'yi destekleyen bir kod dilinde hata ayıklarken Düzenle ve Devam Etme hata iletisi görüntülenir, ancak yaptığınız kod değişiklikleri için Düzenle ve Devam Etme kullanılamaz. Hata iletisi daha ayrıntılı bir açıklama sağlar. İletişim kutusuna yanıt vermek için **Tamam'ı** seçerek iletişim kutusunu kapatın ve düzenleme denemesini iptal edin.

Bu hata iletisinin olası nedenleri şunlardır:

- Bu kodu düzenlemeye SQL Server çalışıyor.
- İyileştirilmiş kodu düzenlemeye çalışma. Bir yayın derlemesi olan bir hata ayıklama derlemesi için geçiş yapmak zorunda olabilir.
- Hata ayıklayıcıda duraklatılmış olarak değil, çalışırken kodu düzenlemeye çalışırken. Kesme [noktası ayarlamayı ve](../debugger/using-breakpoints.md)duraklatılmış sırada kodu düzenlemeyi deneyin.
- Yalnızca yönetilemeyen hata ayıklama etkinleştirildiğinde yönetilen kodu düzenlemeye çalışma. Düzenle ve Devam Etme karma mod hata [ayıklama ile çalışmıyor.](../debugger/how-to-debug-in-mixed-mode.md)
- Programlama dilinizin Düzenle ve Devam Etme tarafından desteklemez bir kod değişikliği yapma. Daha fazla bilgi [için, C#](supported-code-changes-csharp.md)içinde desteklenen kod [değişiklikleri,](supported-code-changes-csharp.md)Düzenle ve Devam Visual Basic'da desteklenmeyen düzenlemeler ve desteklenen C++ kod değişiklikleri ile ilgili [makalelere bakın.](supported-code-changes-cpp.md)
- Hata ayıklamayı Hata Ayıklama menüsünden başlatma yerine, bağlı olduğunuz bir uygulamada kodu **düzenlemeye** çalışma.
- Dr. Watson dökümünde hata ayıklarken kodu düzenlemeye çalışma.
- İşlenemez bir özel durum oluştuğunda kod düzenlemeye çalışıldı ve İşlenemez özel durumlarda çağrı yığınını **geriye** doğru izleme seçeneği seçilmedi.
- Katıştırılmış çalışma zamanı uygulamasında hata ayıklarken kodu düzenlemeye çalışma.
- 64 bit uygulama hedefiyle .NET Framework 4.5.1'den önceki bir sürümü kullanarak yönetilen kodu düzenlemeye çalışırken. 4.5.1'.NET Framework önceki sürümlerde Düzenle ve Devam'ı kullanmak için, Gelişmiş Derleyici ayarı Özellikler Derleme sekmesinde hedefi **x86** **\<ProjectName>**  >    >   **olarak** ayarlayın.
- Hata ayıklama sırasında değiştirilmiş ve yeniden yüklenmiş bir derlemede kodu düzenlemeye çalışma.
- Yüklenmemiş bir derlemede kodu düzenlemeye çalışma.
- Uygulamanın eski bir sürümünde hata ayıklamaya başlayarak, en son sürümde derleme hataları vardır.

Daha fazla bilgi için bkz.
- [C++ Düzenle ve Devam Edin blog gönderisi](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)
- [Desteklenen kod değişiklikleri (C++)](../debugger/supported-code-changes-cpp.md)
- [Düzenle ve Devam Et](../debugger/edit-and-continue.md)