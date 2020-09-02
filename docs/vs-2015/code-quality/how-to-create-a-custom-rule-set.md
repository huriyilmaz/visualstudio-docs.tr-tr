---
title: 'Nasıl yapılır: özel kural kümesi oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6e4aef02a2bb320112d7d268da28cf66b1ec6751
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657442"
---
# <a name="how-to-create-a-custom-rule-set"></a>Nasıl yapılır: Özel Kural Kümesi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

, Ve ' de, ve ' de, [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] [!INCLUDE[vsPro](../includes/vspro-md.md)] kod analizi ile ilişkili belirli proje ihtiyaçlarını karşılamak için özel bir *kural kümesi* oluşturabilir ve değiştirebilirsiniz. Özel bir kural kümesi oluşturmak için, kural kümesi düzenleyicisinde bir veya daha fazla standart kural kümesi açarsınız. Daha sonra belirli kuralları ekleyebilir veya kaldırabilir ve kod analizi bir kuralın ihlal edildiğini belirlediğinde oluşan eylemi değiştirebilirsiniz.

 Yeni bir özel kural kümesi oluşturmak için yeni bir dosya adı kullanarak bu dosyayı kaydedersiniz. Özel kural kümesi projeye otomatik olarak atanır.

## <a name="opening-the-rule-set-editor"></a>Kural kümesi Düzenleyicisini açma

#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>Kural kümesi düzenleyicisinde boş bir kural kümesi dosyasını açmak için

1. **Dosya** menüsünde [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , **Yeni** ' nin üzerine gelin ve ardından **Dosya**' ya tıklayın.

2. **Yeni dosya** iletişim kutusunda, **yüklü şablonlar** listesinde **genel** ' i tıklatın ve ardından **kod analizi kural kümesi**' ni seçin.

3. Kural kümesi Düzenleyicisi görünür. Düzenleyici listesinde hiçbir kural seçilmedi.

#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Tek bir var olan kural kümesinden özel bir kural oluşturmak için

1. Çözüm Gezgini, projeye sağ tıklayın ve ardından **Özellikler**' i seçin.

2. **Özellikler** sekmesinde, **Kod Analizi**' ne tıklayın.

3. **Kural kümesi** açılan listesinde aşağıdakilerden birini yapın:

   - Özelleştirmek istediğiniz kural kümesini seçin.

     \- veya

   - **\<Browse...>** Listede olmayan mevcut bir kural kümesini belirtmek için seçin.

4. Kural kümesi düzenleyicisinde kuralları göstermek için **Aç** ' a tıklayın.

#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>Birden çok var olan kural kümesinden özel bir kural kümesi oluşturmak için

1. Çözüm Gezgini, projeye sağ tıklayın ve ardından **Özellikler**' i seçin.

2. **Özellikler** sekmesinde, **Kod Analizi**' ne tıklayın.

3. **\<Choose multiple rule sets...>** **Bu kural kümesini Çalıştır**' ı seçin.

4. **Kural kümeleri Ekle veya Kaldır** iletişim kutusunda, yeni kural kümesini temel almak istediğiniz kural kümelerini seçin ve ardından **Tamam**' a tıklayın.

5. Yeni kural kümesini kaydedin.

     Yeni kural kümesinin adı **Bu kural kümesini Çalıştır** listesinde seçilir. Bir sonraki adımda kural kümesinin görünen adını değiştirebilirsiniz.

6. Seçim Kural kümesinin görünen adını değiştirmek için, **Görünüm** menüsünde **Özellikler penceresi**' ne tıklayın. **Ad** kutusuna görünen adı yazın.

7. Yeni kural kümesinde belirli kod çözümleme kurallarını eklemek, kaldırmak veya değiştirmek için **Aç**' a tıklayın.

## <a name="modifying-a-rule-set"></a>Bir kural kümesini değiştirme

#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Kural kümesi düzenleyicisinde bir kural kümesini değiştirmek için

- Kural kümesinin görünen adını değiştirmek için, **Görünüm** menüsünde **Özellikler penceresi**' ne tıklayın. **Ad** kutusuna görünen adı girin. Görünen adın dosya adından farklı olduğunu fark edebilirsiniz.

- Grubun tüm kurallarını özel bir kural kümesine eklemek için grubun onay kutusunu seçin. Grubun tüm kurallarını kaldırmak için onay kutusunu temizleyin.

- Özel kural kümesine belirli bir kural eklemek için, kuralın onay kutusunu seçin. Kuralı kural kümesinden kaldırmak için onay kutusunu temizleyin.

- Bir kod analizinde bir kural ihlal edildiğinde gerçekleştirilecek eylemi değiştirmek için, kural için **eylem** alanına tıklayın ve ardından aşağıdaki değerlerden birini seçin:

     **Uyar** -bir uyarı oluşturur.

     **Hata** -bir hata oluşturur.

     **Hiçbiri** -kuralı devre dışı bırakır. Bu eylem kural kümesinden kuralı kaldırma ile aynıdır.

## <a name="changing-the-rule-set-editor-display"></a>Kural kümesi Düzenleyicisi görüntüsünü değiştirme

#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Kural kümesi Düzenleyicisi araç çubuğunu kullanarak kural kümesi düzenleyicisinde Alanları gruplandırmak, filtrelemek veya değiştirmek için

- Tüm gruplardaki kuralları genişletmek için **Tümünü Genişlet**' e tıklayın.

- Tüm gruplardaki kuralları daraltmak için **Tümünü Daralt**' a tıklayın.

- Kuralların gruplandırıldığı alanı değiştirmek için **Gruplandırma ölçütü** listesinden alanı seçin. Gruplandırılmamış kuralları göstermek için öğesini seçin **\<None>** .

- Kural sütunlarındaki alanları eklemek veya kaldırmak için **sütun seçenekleri**' ye tıklayın.

- Geçerli çözüm için geçerli olmayan kuralları gizlemek için **geçerli çözüm için geçerli olmayan kuralları gizleyin**.

- Hata eyleminin atandığı kuralları gösterme ve gizleme arasında geçiş yapmak için, **kod çözümleme hataları oluşturabilen kuralları göster**' e tıklayın.

- Uyarı eyleminin atandığı kuralları gösterme ve gizleme arasında geçiş yapmak için, **Kod Analizi uyarıları oluşturabilen kuralları göster**' e tıklayın.

- **Hiçbiri** eyleminin atandığı kuralları gösterme ve gizleme arasında geçiş yapmak için, **etkin olmayan kuralları göster**' e tıklayın.

- Geçerli kural kümesine Microsoft varsayılan kural kümelerini eklemek veya kaldırmak için **alt kural kümelerini Ekle veya Kaldır**' a tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: yönetilen kod proje](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) [kod analizi kural kümesi başvurusu](../code-quality/code-analysis-rule-set-reference.md) için kod analizini yapılandırma
