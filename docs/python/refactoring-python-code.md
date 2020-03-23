---
title: Refactor Python kodu
description: Visual Studio, tanımlayıcıları yeniden adlandırarak, yöntemleri ayıklayarak, içeri alma eklemeyi ve kullanılmayan içeri aktarımları kaldırarak Python kodunu yeniden düzenlemeyi kolaylaştırır.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: db1a551e20c597f98052471910bcb696c878675f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62429904"
---
# <a name="refactor-python-code"></a>Refactor Python kodu

Visual Studio, Python kaynak kodunuzu otomatik olarak dönüştürmek ve temizlemek için çeşitli komutlar sağlar:

- Seçili bir sınıfı, yöntemi veya değişken adını [yeniden adlandır](#rename)
- [Ayıklama yöntemi](#extract-method) seçili koddan yeni bir yöntem oluşturur
- [İçe aktarma ekle,](#add-import) eksik bir alma eklemek için akıllı etiket sağlar
- [Kullanılmayan içeri aktarımları kaldırma](#remove-unused-imports) kullanılmayan içeriakları kaldırır

## <a name="rename"></a>Yeniden Adlandır

1. Yeniden adlandırmak ve yeniden **adlandırmak**istediğiniz tanımlayıcıyı sağ tıklatın veya bu tanımlayıcıyı bu tanımlayıcıya yerleştirin ve **Yeniden** > **Düzenleme** > **Menüsü** komutunu **(F2)** seçin.
2. Görünen **Yeniden Adlandır** iletişim kutusunda, tanımlayıcının yeni adını girin ve **Tamam'ı**seçin:

   ![Yeni identifer adı için komut istemini yeniden adlandırma](media/code-refactor-rename-1.png)

3. Bir sonraki iletişim kutusunda, kodunuzdaki dosyaları ve örnekleri seçin; belirli değişikliği önizlemek için herhangi bir örneği seçin:

   ![Değişikliklerin uygulanacağı yeri seçmek için iletişim kutusunu yeniden adlandır](media/code-refactor-rename-2.png)

4. Kaynak kod dosyalarınızda değişiklik yapmak için **Uygula'yı** seçin. (Bu eylem geri alınabilir.)

## <a name="extract-method"></a>Ayıklama metodu

1. Ayrı bir yönteme ayıklamak için kod satırlarını veya ifadeyi seçin.
2.  > **Refactor****Extract yöntemini** **edit** > et komutunu seçin veya **Ctrl**+**R** > **M**yazın.
3. Görünen iletişim kutusunda, yeni bir yöntem adı girin, onu nereye ayıklamak için belirtin ve kapatma değişkenlerini seçin. Kapatma için seçilmedimişdeğişkenler yöntem bağımsız değişkenlerine dönüştürüldü:

   ![Ayıklama yöntemi iletişim kutusu](media/code-refactor-extract-method-1.png)

4. **Tamam'ı** seçin ve kod buna göre değiştirilir:

   ![Bir yöntem ayıklamanın etkisi](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>Alma ekle

Bakıcıyı tür bilgisi olmayan bir tanımlayıcıya yerleştirdiğinizde, Visual Studio komutları gerekli `import` veya `from ... import` ifadeyi ekleyen akıllı bir etiket (kodun solundaki ampul simgesi) sağlar:

![Alma akıllı etiketi ekleme](media/code-refactor-add-import-1.png)

Visual Studio, mevcut proje ve standart kitaplıkta üst düzey paketler ve modüller için tamamlamalar sunmaktadır. `import` Visual Studio `from ... import` ayrıca alt modüller ve alt paketlerin yanı sıra modül üyeleri için de tamamlanmalar sunmaktadır. Tamamlamalar işlevleri, sınıfları veya dışa aktarılan verileri içerir. Her iki seçeneğin seçilmesi, diğer içeri almalardan sonra ifadeyi `from ... import` dosyanın en üstüne veya aynı modül zaten içe aktarılırsa varolan bir ekstreye ekler.

![Alma ekleme nin sonucu](media/code-refactor-add-import-2.png)

Visual Studio, bir modülde gerçekte tanımlanmayan, başka bir modüle içe aktarılan ancak içe aktarmayı yapan modülün çocukları olmayan modüller gibi üyeleri filtrelemeye çalışır. Örneğin, birçok modül `import sys` yerine `from xyz import sys`, bu yüzden modülleri hariç `sys` `__all__` `sys`bir üye eksik olsa bile diğer modüllerden içe aktarma için bir tamamlanma görmüyorum.

Benzer şekilde, Visual Studio diğer modüllerden veya yerleşik ad alanından alınan işlevleri filtreler. Örneğin, bir modül `settrace` işlevi `sys` modülden aktarırsa, teorik olarak bu modülden içe aktarabilirsiniz. Ama doğrudan kullanmak `import settrace from sys` en iyisidir, ve bu yüzden Visual Studio özellikle bu ifadeyi sunuyor.

Son olarak, bir şey normalde dışlanmış olacak ancak dahil edilecek başka değerler varsa (örneğin, ad modülde bir değer atandığı için), Visual Studio yine de içe aktarmayı hariç tutar. Bu davranış, başka bir modülde tanımlandığı için değerin dışa aktarılmaması gerektiğini varsayar ve bu nedenle ek atama, dışa aktarılmayan sahte bir değer olabilir.

## <a name="remove-unused-imports"></a>Kullanılmayan içeri aktarımları kaldırma

Kod yazarken, hiç kullanılmayan modüller `import` için deyimlerle birlikte olmak kolaydır. Visual Studio kodunuzu çözümlediği için, alınan `import` adın deyimin oluştuğu yerin altındaki kapsam içinde kullanılıp kullanılmadığına bakarak bir deyimin gerekli olup olmadığını otomatik olarak belirleyebilir.

Düzenleyicinin herhangi bir yerine sağ tıklayın ve **Tüm Kapsamlardan** veya yalnızca **Geçerli Kapsam'tan**kaldırma seçenekleri sunan **İçeriak**Kaldır'ı seçin:

![İçeri aktarım menüsünü kaldırma](media/code-refactor-remove-imports-1.png)

Visual Studio daha sonra kodiçin uygun değişiklikleri yapar:

![İthalatı kaldırmanın etkisi](media/code-refactor-remove-imports-2.png)

Visual Studio'nun kontrol akışını hesaba katmadığını unutmayın; bir deyim önce `import` bir ad kullanarak aslında ad kullanılmış gibi kabul edilir. Visual Studio ayrıca `from __future__` tüm içeri almaları, bir sınıf tanımı içinde `from ... import *` gerçekleştirilen içeri aktarımları ve deyimleri de yok sayar.
