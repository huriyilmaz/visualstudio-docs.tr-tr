---
title: UML sıralı diyagramlarındaki parçalar ile denetim akışını açıklama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.interactionoperand
- vs.teamarch.sequencediagram.combinedfragment
helpviewer_keywords:
- UML sequence diagrams, control flow
- UML sequence diagrams, fragments
- sequence diagrams, fragments
- sequence diagrams, control flow
ms.assetid: efcc0949-be7e-4cf4-99ef-47c36b3803ae
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40f48891107c2eb3250b6b050e00c3650812d386
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669810"
---
# <a name="describe-control-flow-with-fragments-on-uml-sequence-diagrams"></a>Denetim akışını UML sıralı diyagramlarında parçalarla açıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML sıralı diyagramında, *Birleşik parçalar* döngüleri, dalları ve diğer alternatifleri göstermenizi sağlar.

 Birleşik bir parça bir veya daha fazla *etkileşim işleneninden*oluşur ve bunların her biri bir veya daha fazla ileti, etkileşim kullanımı veya Birleşik parçalar barındırır.

> [!NOTE]
> Bu konu, sıralı diyagramlarda parçalar hakkındadır. UML sıralı diyagramlarını okuma hakkında daha fazla bilgi için bkz. [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md). UML sıralı diyagramları çizme hakkında daha fazla bilgi için bkz. [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).

 ![İki etkileşim Işleneniyle Birleşik parça](../modeling/media/uml-seqfragments.png "UML_SeqFragments")

 Şekilde gösterilen öğeler aşağıdaki gibidir.

1. Birleşik parça. Birçok Birleşik parça türü vardır. Bu örnek, diğer ileti sıralarının gerçekleşebileceğini göstermek için kullanabileceğiniz alt Birleşik bir parçadır.

2. Etkileşim işlenenleri. Her Birleşik parça, iletiler, etkileşim kullanımları ve daha küçük Birleşik parçalar içerebilen en az bir etkileşim işleneni içerir. Bu örnekte, alt Birleşik parçanın iki farklı ileti dizisini gösteren iki etkileşim işlemi vardır.

3. Her etkileşim işlenenini, içine tıklayarak ayrı olarak seçebilirsiniz. Bu örnekte, üst etkileşim işleneni seçilir, böylece sınırının görünebilmesini sağlayabilirsiniz. Genellikle, yalnızca etkileşim işlenenleri arasındaki ayırma satırı görünür.

    > [!NOTE]
    > En iyi etkileşim işlenenini seçmek için, Birleşik parçanın üst kısmına çok yakın tıklamamalıdır.

4. Koruma. Her etkileşim işlenenini bir Guard 'a verebilirsiniz. Bu, etkileşim işleneni içindeki iletilerin gerçekleştirileceği koşulu açıklar.

## <a name="creating-combined-fragments"></a>Birleşik parçalar oluşturma
 Oluşturabileceğiniz parça türlerinin listesi için bkz. [birleşik parça türleri](#KindsOfFragment).

#### <a name="to-create-a-combined-fragment"></a>Birleşik bir parça oluşturmak için

1. Tek bir ileti veya bir dizi ileti seçin, hepsi aynı yaşam çizgisinde veya yürütme oluşumunda başlar.

   > [!NOTE]
   > Birden fazla ileti seçerseniz, kesintisiz bir sıra oluşturmaları gerekir.

2. İletilerden birine sağ tıklayın, şununla **çevreye**gelin ve ardından istediğiniz Birleşik parça türüne tıklayın, örneğin **alt Birleşik parça**gibi.

    Yeni bir Birleşik parça görüntülenir. Başlık, **alt**gibi seçtiğiniz Birleştirilmiş parçanın türünü gösterir.

    Birleşik parçanın içinde, seçtiğiniz iletileri içeren bir parça vardır.

   Bazı Birleşik parça türlerine daha fazla etkileşim işlenenleri ekleyebilirsiniz.

   Birleşik bir parçanın içindeki iletileri yeniden düzenledikten sonra, Birleşik parça çerçevesini yeniden boyutlandırmak için kısayol menüsünde **düzeni yeniden Düzenle** ' yi seçin.

#### <a name="to-add-a-new-interaction-operand-to-a-combined-fragment"></a>Birleşik parçaya yeni bir etkileşim işleneni eklemek için

1. Etkileşim işleneni içindeki boş bir alana (2), içerilen parçaların dışında ve Birleşik parçaların başlığının altına sağ tıklayın.

2. **Ekle**' ye gelin.

3. Daha **önce etkileşim işleneni**veya **sonrasında etkileşim işleneni**' ne tıklayın.

4. İleti araçlarını kullanarak veya mevcut iletileri kopyalayıp yapıştırarak yeni etkileşim işleneninin içine iletiler ekleyebilirsiniz.

   Bir etkileşim işleneninin **Guard** özelliğini, içindeki iletilerin gerçekleştirildiği koşulları açıklayan şekilde ayarlayabilirsiniz. Örneğin, bir **döngü** Birleşik parçasında, döngünün devam ettiği koşulu belirtmek için Guard 'ı kullanabilirsiniz. **Alt** Birleşik bir parçada, her etkileşim işleneni için ayrı bir koşul belirtebilirsiniz.

#### <a name="to-set-the-guard-of-an-interaction-operand"></a>Bir etkileşim işleneninin korumasını ayarlamak için

1. Tüm içerilen parçaların dışında, etkileşim işleneni içindeki boş bir alana tıklayın (2).

    Etkileşim işleneni ve koruma koşulunun çevresinde bir seçim kenarlığı görünür.

    **Özellikler** penceresindeki başlık, **etkileşim işlenenini**gösterir.

2. Koruma koşulunu yazın.

    Koşul, parçanın üst kısmında görünür (4).

   Bazı birleştirilmiş parça türlerinin özelliklerini ayarlayabilirsiniz.

#### <a name="to-set-or-view-the-properties-of-a-combined-fragment"></a>Birleşik parçanın özelliklerini ayarlamak veya görüntülemek için

- Birleşik parçanın başlığına sağ tıklayın ve ardından **Özellikler**' e tıklayın.

    > [!NOTE]
    > Farklı türlerde Birleşik parçaların farklı özellikleri vardır.

## <a name="KindsOfFragment"></a>Birleşik parça türleri

### <a name="fragments-describing-control-flow"></a>Denetim akışını açıklayan parçalar
 Basit bir sıra diyagramı yalnızca bir adet tipik sırayı gösterir. Farklı durumlarda gerçekleşebileceği çeşitlemeleri anlatmak için aşağıdaki Birleşik parça türlerini kullanabilirsiniz.

|Parça türü|Açıklama|
|-------------------|-----------------|
|**Et**|İsteğe bağlı. Gerçekleşebilen veya gerçekleşmeyecek bir diziyi barındırır. Koruma, altında gerçekleştiği koşulu belirtebilirsiniz.|
|**Alternatif**|Alternatif ileti dizilerini içeren parçaların bir listesini içerir. Her gün yalnızca bir sıra oluşur.<br /><br /> Her parçaya, hangi koşulun çalıştırılacağını göstermek için bir koruyucu koyabilirsiniz. Diğer bir koruyucu **, başka bir** koruyucu doğru değilse çalışması gereken bir parçayı gösterir. Tüm korumalara yanlışı varsa ve **başka**bir yoksa, parçaların hiçbiri yürütülür.|
|**Gerçekleştirmek**|Parça birkaç kez yinelenir. Koruma sırasında tekrarlanacak koşulu belirtebilirsiniz.<br /><br /> Döngü Birleşik parçaları **Min** ve **Max**özelliklerine sahiptir; bu, parçanın tekrarlanma sürebileceği en düşük ve en yüksek sayıyı gösterir. Varsayılan değer kısıtlama değildir.|
|**Sonundan**|Bu parça yürütülürse, sıranın geri kalanı terk edilir. Break 'in gerçekleşeceği koşulu belirtmek için Guard 'ı kullanabilirsiniz.|
|**İ**|Dir. Parçalardaki olaylar araya eklenebilir.|
|**Başlatma**|Bir par veya Seq parçası içinde kullanılır. Bu parçadaki iletilerin diğer iletilerle birlikte aralanmamış olması gerektiğini gösterir.|
|**Sıra**|İki veya daha fazla işlenen parçası var. Aynı yaşam çizgisini içeren iletiler parçalar sırasıyla gerçekleşmelidir. Aynı yaşam çizgilerini içermeyen, farklı parçalardan iletiler paralel olarak eklenebilir.|
|**Sert**|İki veya daha fazla işlenen parçası var. Parçalar verilen sırada gerçekleşmelidir.|

### <a name="fragments-about-how-to-interpret-the-sequence"></a>Sıranın nasıl yorumlanacağı hakkında parçalar
 Varsayılan olarak, sıralı diyagram, gerçekleşebileceğini bir dizi mesaj bildirir. Çalışan sistemde, diyagramda göstermeyi seçmediğiniz başka iletiler olabilir.

 Bu yorumu değiştirmek için aşağıdaki parça türleri kullanılabilir.

|Parça türü|Açıklama|
|-------------------|-----------------|
|**Seçmeyi**|Bu parçanın açıkladığı iletilerin bir listesini belirtir. Diğer iletiler çalışan sistemde gerçekleşebilir, ancak bu açıklamanın amaçları için önemli değildir.<br /><br /> **Iletileri messages** özelliğine yazın.|
|**Yoksay**|Bu parçanın betimleyen iletilerinin listesi. Bunlar çalışan sistemde gerçekleşebilir, ancak bu açıklamanın amaçları için önemli değildir.<br /><br /> **Iletileri messages** özelliğine yazın.|
|**Vermediğini**|İşlenen parçası yalnızca geçerli dizileri belirtir. Genellikle bir dikkate alma veya yoksayma parçası içinde kullanılır.|
|**Neg**|Bu parçada gösterilen sıra gerçekleşmemelidir. Genellikle bir dikkate alma veya yoksayma parçası içinde kullanılır.|

## <a name="see-also"></a>Ayrıca Bkz.
 [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md) [UML sıralı DIYAGRAMLAR: başvuru](../modeling/uml-sequence-diagrams-reference.md) [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md)
