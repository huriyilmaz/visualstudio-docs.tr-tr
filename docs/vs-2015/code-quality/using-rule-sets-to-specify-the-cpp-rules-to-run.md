---
title: Çalıştırılacak C++ kuralları belirtmek Için kural kümeleri kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: ff105af1d817613b324e1158130457eb906c753f
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277859"
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>Çalıştırılacak C++ Kurallarını Belirtmek için Kural Kümeleri Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] ve [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)]' de, kod analizi ile ilişkili belirli proje ihtiyaçlarını karşılamak için özel bir *kural kümesi* oluşturabilir ve değiştirebilirsiniz. Özel C++ bir kural kümesi oluşturmak Için, VISUAL Studio IDEC++ 'de bir C/Project açık olmalıdır. Daha sonra kural kümesi düzenleyicisinde bir standart kural kümesi açıp, belirli kuralları ekleyip kaldırarak ve isteğe bağlı olarak, kod analizi bir kuralın ihlal edildiğini belirlediğinde oluşan eylemi değiştirirsiniz.  
  
 Yeni bir özel kural kümesi oluşturmak için yeni bir dosya adı kullanarak bu dosyayı kaydedersiniz. Özel kural kümesi projeye otomatik olarak atanır.  
  
## <a name="opening-the-rule-set-editor"></a>Kural kümesi Düzenleyicisini açma  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Tek bir var olan kural kümesinden özel bir kural oluşturmak için  
  
1. Çözüm Gezgini ' de, proje için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.  
  
2. **Özellikler** sekmesinde, **Kod Analizi**' ni seçin.  
  
3. **Kural kümesi** açılan listesinde aşağıdakilerden birini yapın:  
  
   - Özelleştirmek istediğiniz kural kümesini seçin.  
  
     \- veya-  
  
   - **\<gözatmaya seç...** listede olmayan var olan bir kural kümesini belirtmek için >.  
  
4. Kural kümesi düzenleyicisinde kuralları göstermek için **Aç** ' ı seçin.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Kural kümesi düzenleyicisinde bir kural kümesini değiştirmek için  
  
- Kural kümesinin görünen adını değiştirmek için, **Görünüm** menüsünde **Özellikler penceresi**' ni seçin. **Ad** kutusuna görünen adı girin. Görünen adın dosya adından farklı olduğunu fark edebilirsiniz.  
  
- Grubun tüm kurallarını özel bir kural kümesine eklemek için grubun onay kutusunu seçin. Grubun tüm kurallarını kaldırmak için onay kutusunu temizleyin.  
  
- Özel kural kümesine belirli bir kural eklemek için, kuralın onay kutusunu seçin. Kuralı kural kümesinden kaldırmak için onay kutusunu temizleyin.  
  
- Bir kod analizinde bir kural ihlal edildiğinde gerçekleştirilecek eylemi değiştirmek için, kural için **eylem** alanını seçin ve ardından aşağıdaki değerlerden birini seçin:  
  
     **Uyar** -bir uyarı oluşturur.  
  
     **Hata** -bir hata oluşturur.  
  
     **Hiçbiri** -kuralı devre dışı bırakır. Bu eylem kural kümesinden kuralı kaldırma ile aynıdır.  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Kural kümesi Düzenleyicisi araç çubuğunu kullanarak kural kümesi düzenleyicisinde Alanları gruplandırmak, filtrelemek veya değiştirmek için  
  
- Tüm gruplardaki kuralları genişletmek için **Tümünü Genişlet**' i seçin.  
  
- Tüm gruplardaki kuralları daraltmak için **Tümünü Daralt**' ı seçin.  
  
- Kuralların gruplandırıldığı alanı değiştirmek için **Gruplandırma ölçütü** listesinden alanı seçin. Gruplandırılmamış kuralları göstermek için **\<yok >** seçin.  
  
- Kural sütunlarındaki alanları eklemek veya kaldırmak için **sütun seçenekleri**' yi seçin.  
  
- Geçerli çözüm için geçerli olmayan kuralları gizlemek için **geçerli çözüm için geçerli olmayan kuralları gizle**' yi seçin.  
  
- Hata eyleminin atandığı kuralları gösterme ve gizleme arasında geçiş yapmak için, **Kod Analizi hataları oluşturabilen kuralları göster**' i seçin.  
  
- Uyarı eyleminin atandığı kuralları gösterme ve gizleme arasında geçiş yapmak için, **Kod Analizi uyarıları oluşturabilen kuralları göster**' i seçin.  
  
- **Hiçbiri** eyleminin atandığı kuralları gösterme ve gizleme arasında geçiş yapmak için, **etkin olmayan kuralları göster**' i seçin.  
  
- Geçerli kural kümesine Microsoft varsayılan kural kümelerini eklemek veya kaldırmak için **alt kural kümelerini Ekle veya Kaldır**' ı seçin.
