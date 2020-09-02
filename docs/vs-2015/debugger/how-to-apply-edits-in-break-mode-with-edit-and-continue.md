---
title: 'Nasıl yapılır: Düzenle ve devam et ile kesme modunda düzenleme uygulama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c04dc0ae6e5272d2544ad7436fa7ca516c9a022
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64795661"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue"></a>Nasıl Yapılır: Düzenle ve Devam Et ile Kesme Modunda Düzenlemeleri Uygulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodunuzu kesme modunda düzenlemek için Düzenle ve devam et ' i kullanabilir ve sonra yürütmeyi durdurup yeniden başlatmadan devam edebilirsiniz.  
  
 Düzenle ve devam et aşağıdaki hata ayıklama senaryolarında kullanılamaz:  
  
- Karışık mod (Yerel/yönetilen) hata ayıklama.  
  
- SQL hata ayıklaması.  
  
- Dr. Watson dökümünü hata ayıklama.  
  
- İşlenmeyen özel **durumlar üzerinde çağrı yığınını geri bırakma** seçeneği seçili değilse, işlenmemiş bir özel durumdan sonra kodu düzenleyebilirsiniz.  
  
- Gömülü çalışma zamanı uygulamasında hata ayıklama.  
  
- **Hata ayıklama** menüsünden **Başlangıç** ile uygulamayı çalıştırmak yerine, **Attach** ile bir uygulamada hata ayıklama.  
  
- İyileştirilmiş kodda hata ayıklama.  
  
- Hedef 64 bitlik bir uygulama olduğunda yönetilen kodda hata ayıklama. Düzenle ve devam et ' i kullanmak istiyorsanız, hedefi x86 olarak ayarlamanız gerekir. (_Proje_**özellikleri**, **derleme** sekmesi, **Gelişmiş derleyici** ayarı.).  
  
- Derleme hataları nedeniyle yeni bir sürümden sonra kodunuzun eski bir sürümünde hata ayıklama başarısız oldu.  
  
### <a name="to-edit-code-in-break-mode"></a>Kodu kesme modunda düzenlemek için  
  
1. Aşağıdakilerden birini yaparak kesme moduna girin:  
  
    - Kodunuzda bir kesme noktası ayarlayın, ardından **Hata Ayıkla** menüsünden **hata ayıklamayı Başlat** ' ı seçin ve uygulamanın kesme noktasına gelmesini bekleyin.  
  
         veya  
  
    - Hata ayıklamayı başlatın ve **Hata Ayıkla** menüsünden **Tümünü kes** ' i seçin.  
  
         veya  
  
    - Bir özel durum oluştuğunda,**özel durum Yardımcısı**üzerinde **düzenlemesi etkinleştir** ' i seçin.  
  
2. İstediğiniz ve geçerli kod değişikliklerini yapın.  
  
     Daha fazla bilgi için [Visual Basic Düzenle ve devam et ' de desteklenmeyen düzenlemeler](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)bölümüne bakın.  
  
    > [!NOTE]
    > Düzenle ve devam et tarafından izin verilmeyen bir kod değişikliği yapmaya çalışırsanız, düzenlemeniz mor dalgalı bir çizgiyle altı çizili olur ve Görev Listesi bir görev görüntülenir. Geçersiz kod değişikliğini geri yüklemediğiniz takdirde kod yürütmeye devam edemeyeceksiniz.  
  
3. **Hata Ayıkla** menüsünde, yürütmeyi sürdürmek için **devam** ' a tıklayın.  
  
     Kodunuz artık projeye eklenen ve uygulanan düzenlemelerinizle yürütülür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic Düzenle ve devam et 'de desteklenmeyen düzenlemeler](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Düzenle ve Devam Et (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
