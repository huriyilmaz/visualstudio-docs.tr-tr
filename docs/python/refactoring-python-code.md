---
title: Python kodunu yeniden düzenleme
description: Visual Studio tanımlayıcıları yeniden adlandırarak, yöntemleri ayıklar, içeri aktarmalar ekleyerek ve kullanılmayan içeri aktarmaları kaldırarak Python kodunu yeniden düzenlemeyi kolaylaştırır.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 21556deca0da180d145b11ed155e0d8b993301a00362e9a67a9af1d4aa02f9a6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121229708"
---
# <a name="refactor-python-code"></a>Python kodunu yeniden düzenleme

Visual Studio Python kaynak kodunuzu otomatik olarak dönüştürmek ve temizlemek için çeşitli komutlar sağlar:

- [Yeniden](#rename) adlandırma seçili bir sınıfı, yöntemi veya değişken adını yeniden adlandırıyor
- [Ayıklama yöntemi](#extract-method) seçilen koddan yeni bir yöntem oluşturur
- [İçeri aktarma ekle,](#add-import) eksik içeri aktarma eklemek için akıllı bir etiket sağlar
- [Kullanılmayan içeri aktarmaları kaldırma,](#remove-unused-imports) kullanılmayan içeri aktarmaları kaldırır

## <a name="rename"></a>Rename

1. Yeniden adlandırmak istediğiniz tanımlayıcıya sağ tıklayın ve Yeniden Adlandır'ı seçin veya giriş imtiyazı bu tanımlayıcıya ek olarak Yeniden DüzenlemeYi Düzenle menü  >    >   komutunu (**F2) seçin.**
2. Görüntülenen Yeniden **Adlandır** iletişim kutusunda tanımlayıcı için yeni adı girin ve Tamam'ı **seçin:**

   ![Yeni kimlikli ad için yeniden adlandırma istemi](media/code-refactor-rename-1.png)

3. Sonraki iletişim kutusunda, kodunuzda yeniden adı değiştirmek için uygulanacak dosyaları ve örnekleri seçin; belirli bir değişikliğin önizlemesini görmek için herhangi bir örneği seçin:

   ![Değişiklikleri nereye uygulayacaklarını seçmek için Yeniden Adlandır iletişim kutusu](media/code-refactor-rename-2.png)

4. Kaynak **kod** dosyalarınıza değişiklik yapmak için Uygula'ya seçin. (Bu eylem geri alınamaz.)

## <a name="extract-method"></a>Ayıklama metodu

1. Ayrı bir yönteme ayıklanan kod satırlarını veya ifadeyi seçin.
2. Yeniden Düzenle  >  **Ayıklama yöntemi menü**  >  **komutunu** seçin veya **Ctrl** + **R**  >  **M yazın.**
3. Görüntülenen iletişim kutusunda yeni bir yöntem adı girin, bu yöntemin nereye ayıklan olduğunu girin ve kapanış değişkenlerini seçin. Kapatma için seçilmemiş değişkenler yöntem bağımsız değişkenlerine çevrildi:

   ![Yöntemi ayıkla iletişim kutusu](media/code-refactor-extract-method-1.png)

4. **Tamam'ı** seçin ve kod uygun şekilde değiştirilir:

   ![Yöntem ayıklamanın etkisi](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>İçeri aktarma ekleme

yazısını tür bilgisi olmayan bir tanımlayıcıya yer Visual Studio, komutları gerekli veya deyimini ekli bir akıllı etiket (kodun sol tarafından ampul simgesi) `import` `from ... import` sağlar:

![İçeri aktarma akıllı etiketi ekleme](media/code-refactor-add-import-1.png)

Visual Studio, geçerli proje ve standart kitaplıkta üst düzey paketler ve `import` modüller için tamamlamalar sunar. Visual Studio modüller ve alt paketlere ek olarak modül üyeleri `from ... import` için tamamlamalar da sunar. Tamamlamalar işlevler, sınıflar veya dışarı aktarıldı verileri içerir. İki seçenek arasında seçim yapmak deyimini dosyanın en üstüne diğer içeri aktarmalardan sonra veya aynı modül zaten içeri aktarılmışsa mevcut `from ... import` bir deyime ekler.

![İçeri aktarma ekleme sonucu](media/code-refactor-add-import-2.png)

Visual Studio, başka bir modüle içeri aktarılan ancak içeri aktarmayı yapan modülün üyesi olmayan modüller gibi aslında tanımlanmamış üyeleri filtrelemeye çalışır. Örneğin, birçok modül yerine kullanır, bu nedenle, modüller hariç bir üye eksik olsa bile diğer modüllerden içeri aktarma için bir `import sys` `from xyz import sys` tamamlama `sys` `__all__` `sys` görmüyorsanız.

Benzer şekilde Visual Studio modüllerden veya yerleşik ad alanlarından içe aktarılan işlevleri filtreler. Örneğin bir modül işlevi modülden `settrace` içeri aktarıyorsa teoride bu `sys` modülden içeri aktarabilirsiniz. Ancak doğrudan kullanmak en iyisidir `import settrace from sys` ve bu nedenle bu Visual Studio özellikle sunar.

Son olarak, normalde bir şey hariç tutulacak ancak dahil edilecek başka değerler varsa (örneğin, modülde ada bir değer atandığı için) Visual Studio içeri aktarmayı dışlar. Bu davranış, değerin başka bir modülde tanımlandığı için dışarı aktarılamaması gerektiğini ve bu nedenle ek atamanın da dışarı aktarlanmamış sahte bir değer olduğunu varsayıyor.

## <a name="remove-unused-imports"></a>Kullanılmayan içeri aktarmaları kaldırma

Kod yazarken hiç kullanılmadan `import` modüllere ilişkin deyimler kolayca kullanılabilir. Kod Visual Studio çözümleyene kadar, deyimin oluştuğu aşağıdaki kapsamda içe aktarılan adın kullanıp kullanılmay durumuna bakarak bir deyimin gerekli olup olmadığını otomatik `import` olarak belirler.

Düzenleyicide herhangi bir yere sağ tıklayın ve İçeri Aktarmaları Kaldır'ı seçerek Tüm Kapsamlar'dan veya yalnızca Geçerli Kapsam'dan kaldırma **seçenekleri sunar:** 

![İçeri aktarmaları kaldır menüsü](media/code-refactor-remove-imports-1.png)

Visual Studio kodda uygun değişiklikleri yapar:

![İçeri aktarmaları kaldırmanın etkisi](media/code-refactor-remove-imports-2.png)

Denetim Visual Studio olmadığını unutmayın; deyiminden önce bir `import` ad kullanmak, aslında kullanılmış gibi kabul edilir. Visual Studio, bir sınıf tanımının içinde ve deyimlerinden gerçekleştirilen tüm içeri `from __future__` aktarmaları da `from ... import *` yoksayar.
