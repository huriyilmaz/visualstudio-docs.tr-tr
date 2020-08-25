---
title: Python kodunu yeniden düzenleme
description: Visual Studio, tanımlayıcıları yeniden adlandırarak, yöntemleri ayıklayarak, içeri aktarmalar ekleyerek ve kullanılmayan içeri aktarmaları kaldırarak Python kodunu yeniden düzenleme kolaylarını kolaylaştırır.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: be93ac7b8bc0659da522abcf6000d97ec05d46b9
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801340"
---
# <a name="refactor-python-code"></a>Python kodunu yeniden düzenleme

Visual Studio, Python kaynak kodunuzu otomatik olarak dönüştürmek ve temizlemek için birkaç komut sağlar:

- [Yeniden adlandırma](#rename) seçili bir sınıfı, yöntemi veya değişken adını yeniden adlandırır
- [Extract yöntemi](#extract-method) seçili koddan yeni bir yöntem oluşturur
- [İçeri aktarma ekleme](#add-import) eksik içeri aktarma eklemek için akıllı etiket sağlar
- [Kullanılmayan içeri aktarmaları kaldır](#remove-unused-imports) kullanılmamış içeri aktarmaları kaldırır

## <a name="rename"></a>Rename

1. Yeniden adlandırmak istediğiniz tanımlayıcıya sağ tıklayın ve **Yeniden Adlandır**' ı seçin veya giriş işaretini bu tanımlayıcıya yerleştirin ve yeniden **düzenleme**  >  **Refactor**  >  **Yeniden Adlandır** menü komutunu (**F2**) seçin.
2. Görüntülenen **Yeniden Adlandır** iletişim kutusunda, tanımlayıcı için yeni bir ad girin ve **Tamam**' ı seçin:

   ![Yeni tanımlayıcı adı için istemi yeniden adlandır](media/code-refactor-rename-1.png)

3. Sonraki iletişim kutusunda, kodunuzun yeniden adlandırmasının uygulanacağı dosya ve örnekleri seçin; belirli bir değişikliği önizlemek için tek bir örnek seçin:

   ![Değişiklikleri nereye uygulanacağını seçmek için iletişim kutusunu yeniden adlandır](media/code-refactor-rename-2.png)

4. Değişiklikleri kaynak kodu dosyalarınızda yapmak için **Uygula** ' yı seçin. (Bu eylem geri alınabilir.)

## <a name="extract-method"></a>Ayıklama metodu

1. Kod satırlarını veya ayrı bir yönteme Ayıklanacak ifadeyi seçin.
2. Yeniden **düzenleme**  >  **Refactor**  >  **ayıklama yöntemini** Düzenle menü komutunu seçin veya **CTRL** + **R**  >  **M**yazın.
3. Görüntülenen iletişim kutusunda yeni bir yöntem adı girin, bunu hangi noktada çıkaracağı belirtin ve tüm kapatma değişkenlerini seçin. Kapanış için seçili olmayan değişkenler metot bağımsız değişkenlerine açıktır:

   ![Metodu Ayıkla iletişim kutusu](media/code-refactor-extract-method-1.png)

4. **Tamam** ' ı seçin ve kod uygun şekilde değiştirilir:

   ![Bir yöntemi ayıklama etkisi](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>İçeri aktarma Ekle

Giriş işaretini tür bilgisi olmayan bir tanımlayıcıya yerleştirdiğinizde, Visual Studio komutları gerekli veya ifadeyi ekleyen akıllı bir etiket (kodun solundaki ampul simgesi) sağlar `import` `from ... import` :

![İçeri aktarma akıllı etiketi ekle](media/code-refactor-add-import-1.png)

Visual Studio `import` , geçerli projede ve standart kitaplıkta en üst düzey paketler ve modüller için tamamlama sağlar. Visual Studio Ayrıca `from ... import` , alt modüller ve alt paketlerin yanı sıra modül üyeleri için de tamamlama sağlar. Tamamlama işlevleri, sınıfları veya aktarılmış verileri içerir. İki seçenekten birini seçmek, başka içeri aktarımlardan sonra dosyanın üst kısmına veya `from ... import` aynı modül zaten içeri aktarılmışsa var olan bir deyime ekler.

![İçeri aktarma eklemenin sonucu](media/code-refactor-add-import-2.png)

Visual Studio, başka bir modülde içeri aktarılan ancak içeri aktarma işlemi yapan modülün alt öğesi olmayan modüller gibi, gerçekten tanımlı olmayan üyeleri filtrelemeye çalışır. Örneğin, yerine pek çok modül kullanıyorsa `import sys` `from xyz import sys` , `sys` modüller hariç dışlayan bir üyenin eksik olması durumunda diğer modüllerden içeri aktarma tamamlamayı görmezsiniz `__all__` `sys` .

Benzer şekilde, Visual Studio başka modüllerden veya yerleşik ad alanından içeri aktarılan işlevlere filtre uygular. Örneğin, bir modül işlevi modülden içeri aktardığında `settrace` `sys` , teorik olarak bu modülden içeri aktarabilirsiniz. Ancak doğrudan kullanmak en iyisidir `import settrace from sys` . bu nedenle, Visual Studio bu ifadeyi özellikle sunmaktadır.

Son olarak, bir şeyler normalde dışlanırsa ancak dahil edilecek diğer değerlere sahipse (örneğin, ad modüldeki bir değer atandığı için), Visual Studio yine de içeri aktarmayı dışlar. Bu davranış, başka bir modülde tanımlandığından değerin verilmemesi gerektiğini varsayar ve bu nedenle ek atama büyük olasılıkla aynı zamanda verilemeyen bir kukla değer olabilir.

## <a name="remove-unused-imports"></a>Kullanılmayan içeri aktarmaları kaldır

Kod yazarken, `import` hiç kullanılmayan modüller için deyimlerle daha kolay bir şekilde bitemez. Visual Studio, kodunuzu analiz ettiğinden, `import` içeri aktarılan adın deyimin gerçekleştiği kapsam içinde kullanılıp kullanılmadığını arayarak otomatik olarak bir deyimin gerekip gerekmediğini otomatik olarak belirleyebilir.

Düzenleyicide herhangi bir yere sağ tıklayın ve **Içeri aktarmaları kaldır**' ı seçerek **tüm kapsamlardan** veya yalnızca **geçerli kapsamdan**kaldırma seçenekleri sunulur:

![İçeri aktarmalar menüsünü kaldır](media/code-refactor-remove-imports-1.png)

Daha sonra Visual Studio, koda uygun değişiklikleri yapar:

![İçeri aktarmaları kaldırma etkisi](media/code-refactor-remove-imports-2.png)

Visual Studio 'Nun denetim akışını hesaba madığını unutmayın; bir `import` deyimin adı, adın gerçekten kullanılmış gibi değerlendirilmesinden önce kullanılması. Visual Studio Ayrıca `from __future__` , bir sınıf tanımının içinde gerçekleştirilen tüm içeri aktarmaları, içeri aktarmaları ve deyimlerden de yoksayar `from ... import *` .
