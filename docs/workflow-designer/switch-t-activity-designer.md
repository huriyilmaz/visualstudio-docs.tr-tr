---
title: İş Akışı Tasarımcısı - Switch &lt; T &gt; Etkinlik Tasarımcısı
description: Switch etkinlik tasarımcısını kullanarak bir Switch etkinliği oluşturma ve yapılandırma hakkında <T> <T> bilgi İş Akışı Tasarımcısı.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 1fc06eaaa7bd54ff42a087016dae30e674de4023
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025361"
---
# <a name="switcht-activity-designer"></a>Switch\<T> Etkinlik Tasarımcısı

Etkinlik, belirtilen bir ifadeyi değerlendirir ve etkinliği ilişkili anahtarı değerlendirmeden alınan değerle eşleşen <xref:System.Activities.Statements.Switch%601> bir etkinlik koleksiyonundan yürütür.

Switch **<T \>** etkinlik tasarımcısı, etkinlik oluşturmak ve yapılandırmak için <xref:System.Activities.Statements.Switch%601> İş Akışı Tasarımcısı.

## <a name="the-switchtactivity"></a>Switch \<T> Etkinliği

Etkinlik <xref:System.Activities.Statements.Switch%601> bir ve sözlüğü <xref:System.Activities.Statements.Switch%601.Expression%2A> <xref:System.Activities.Statements.Switch%601.Cases%2A> içerir. Sözlükte her büyük/küçük harf, bir  anahtar ve karşılık gelen değeri olarak hizmet veren bir etkinlik içeren bir *çiftten oluşur.* Etkinlik, <xref:System.Activities.Statements.Switch%601> <xref:System.Activities.Statements.Switch%601.Expression%2A> 'i değerlendirir ve anahtarların her biri ile karşılaştırıldığında. Bir eşleşme bulunursa ilgili etkinlik yürütülür. Sözlük anahtarlarının, sözlüğün eşitlik karşıtlığı tarafından tanımlanan eşitlik türüne göre benzersiz olması gerektir olduğundan yalnızca bir eşleşme mümkündür. Eşleşme bulunamasa <xref:System.Activities.Statements.Switch%601.Default%2A> etkinlik yürütülür.

## <a name="how-to-use-the-switcht-activity-designer"></a>Switch \<T> Etkinlik Tasarımcısı'nın kullanımı

Araç Kutusunun **Denetim \<T>** Denetimi Flow **Switch** etkinlik **tasarımcısına erişin.** Bunu kullanıcıya bıraktıktan İş Akışı Tasarımcısı, kullanıcının  etkinlikte kullanılan genel T türünü belirtmesine izin vermesi için *Türleri* Seç iletişim kutusunu <xref:System.Activities.Statements.Switch%601> görüntüler. Varsayılan değer **Int32'dir.** T genel *türü* seçildikten sonra iş akışı **tasarımcısına<\> T** tasarımcısına anahtar anahtarı eklenir.

**Switch<T tasarımcısının özellikleri \> aşağıda ve** ardından ve ardından ve ve ardından 2. Bu özelliklerin hepsi özellik kılavuzunda düzenlenebilir. Bunlardan bazıları tasarımcı yüzeyinde de düzenlenebilir.

Aşağıdaki tabloda en kullanışlı özellikler <xref:System.Activities.Statements.Switch%601> ve bunların tasarımcıda nasıl kullanıldıkları açık bulunmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinlik tasarımcısının kolay <xref:System.Activities.Statements.Switch%601> adını belirtir. Varsayılan değer, Switch<Int32'dir. \> Değer, Özellikler penceresinde veya **doğrudan** tasarımcı üst bilgisinde düzenlenebilir.<br /><br /> kesinlikle <xref:System.Activities.Activity.DisplayName%2A> gerekli değildir, ancak bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|Doğru|Hangi büyük/büyük/büyük/büyük harf yürütülecek olduğunu belirlemek için cases koleksiyonunda bulunan anahtarlara karşılaştırmak için kullanılan ifadeyi belirtir.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Eşleşme bulunamasa yürütülen etkinliği belirtir. Tasarımcıda **Etkinlik ekle** düğmesine tıklayarak **etkinliğin bırakılan** Varsayılan kutusunu açın.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Değerlendirilecek servis durumlarını belirtir. Bir olay eklemek için Anahtar **tasarımcısının altındaki** Yeni büyük/küçük harf ekle **düğmesine \<T>** tıklayın. Düğme bir metin kutusuna (Anahtar eklerken seçilen genel tür Dize veya Enum ise \<T> birleşik giriş kutusu) olarak değişir. Durum değeri kutusuna  bir anahtar ekledikten sonra, büyük/küçük harf alanı genişletildi ve olay için yürütme mantığını tanımlamak üzere "Etkinliği buraya bırak" ipucu metninin bulunduğu bir etkinlik bırakabilirsiniz.|

Durum anahtarları çoğaltılmış değil sürece birden çok durum eklenebilir. Aksi takdirde, belirtilen büyük/küçük harf anahtarının zaten mevcut olduğunu ve farklı bir anahtar seçmeniz gerektiğini bildiren bir hata iletişim kutusu görüntülenir. Anahtar **\<T> tasarımcısında,** aynı anda yalnızca bir durum alanı genişletilmiş görünümde olabilir. Bir olay alanı daraltılmış görünümde ise, büyük/küçük harf alanına tıklarsanız bu alan genişler. Daraltılmış bir durum için tasarımcının etkinliğin görünen adını varsa sağ tarafta büyük/küçük harf içinde gösterir. Aksi takdirde, **tıklarsanız durumu** genişleten ve etkinlik eklemenize olanak sağlayan Etkinlik ekle düğmesini gösterir.

Mevcut büyük/küçük harf anahtarına tıklarsanız, büyük/küçük harf anahtarını düzenleyemezsiniz.

Bir durumu silmenin 2 yolu vardır:

- Büyük/son durumu seçin ve silin.

- Durumu seçin, bağlam menüsünü görüntülemek için sağ tıklayın ve Sil'i **seçin.**

Silmek için büyük/büyük/yeni bir harf seçmeniz gerektiğini unutmayın. Bir olay içindeki etkinliği seçmek ve silmek yalnızca etkinliği siler, büyük/küçük harfe değil yalnızca etkinliği siler.

## <a name="see-also"></a>Ayrıca bkz.

- [Denetim Flow](../workflow-designer/control-flow-activity-designers.md)
