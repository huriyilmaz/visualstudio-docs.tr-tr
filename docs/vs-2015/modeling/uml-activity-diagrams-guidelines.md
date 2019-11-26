---
title: 'UML etkinlik diyagramları: yönergeler | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
ms.assetid: fe5dbe96-79ab-483a-b9bc-44d0d1d3efc2
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 692859008891439e4af3d751306bfd3ee6d351e8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298990"
---
# <a name="uml-activity-diagrams-guidelines"></a>UML Etkinlik Diyagramları: Yönergeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da, bir dizi eylem aracılığıyla iş akışı olarak bir iş süreci veya yazılım algoritması betimleyen bir etkinlik diyagramı çizebilirsiniz. Kişiler, yazılım bileşenleri veya cihazlar bu eylemleri gerçekleştirebilir. Video gösterimi için bkz.: [etkinlik diyagramlarını kullanarak Iş Iş akışlarını yakalama](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows).

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Bir UML etkinlik diyagramı oluşturmak için **mimari** menüsünde **Yeni UML veya katman diyagramı**' na tıklayın.

 Bir etkinlik diyagramını birçok amaçla kullanabilirsiniz:

- Bir iş işlemini veya kullanıcılar ile sisteminiz arasındaki iş akışını anlatmak için. Daha fazla bilgi için bkz. [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).

- Kullanım durumunda gerçekleştirilen adımları anlatmak için. Daha fazla bilgi için bkz. [UML Kullanım örneği diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md).

- Bir yöntemi, işlevi veya yazılımda bir işlemi anlatmak için. Daha fazla bilgi için bkz. [uygulamanızın mimarisini modelleme](../modeling/model-your-app-s-architecture.md).

  Bir etkinlik diyagramı çizmek, bir işlemi iyileştirmenize yardımcı olabilir. Varolan bir işlemin diyagramı çok karmaşıksa, işlemin nasıl basitleşebildiğini göz önünde bulundurun.

  Etkinlik diyagramlarındaki öğeler hakkında başvuru bilgileri için bkz. [UML etkinlik diyagramları: başvuru](../modeling/uml-activity-diagrams-reference.md).

## <a name="Relationships"></a>Diğer diyagramlarla ilişki
 Bir iş işlemini veya kullanıcıların sisteminizi kullanma yolunu açıklayan bir etkinlik diyagramı çiziyorsanız, aynı bilgilerin farklı bir görünümünü göstermek için bir kullanım durumu diyagramı çizebilirsiniz. Kullanım durumu diyagramında, eylemleri kullanım örnekleri olarak çizersiniz. Kullanım örneklerine karşılık gelen eylemlerle aynı adı verin. Kullanım örneği görünümünün avantajları şunları yapabilirsiniz:

- Daha büyük eylemler/kullanım örneklerinin ne kadar küçük olursa olduğunu, dahil edilen ilişkiyi kullanarak tek bir diyagramda gösterebilirsiniz.

- Her eylem/kullanım örneğini, yürütmede kullanılan kullanıcılara veya dış sistemlere açık olarak bağlayın.

- Sisteminiz veya bunun her bir ana bileşeni tarafından desteklenen eylemlerin/kullanım örneklerinin sınırlarını çizin.

  Ayrıca, bir yazılım işleminin ayrıntılı tasarımını anlatan bir etkinlik diyagramı çizebilirsiniz.

  Etkinlik diyagramında, eylemler arasında geçirilen veri akışını gösterebilirsiniz. [Veri akışını açıklama](#DataFlows)bölümüne bakın. Ancak bir etkinlik diyagramı, verilerin yapısını tanımlamaz. Bu amaçla, bir UML sınıf diyagramı çizebilirsiniz. Bilgi için bkz. [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md).

## <a name="BasicSteps"></a>Etkinlik diyagramları çizmek için temel adımlar
 Modelleme diyagramlarından herhangi birini oluşturmaya yönelik ayrıntılı adımlar [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md)bölümünde açıklanmıştır.

#### <a name="to-draw-an-activity-diagram"></a>Etkinlik diyagramı çizmek için

1. **Mimari** menüsünde **Yeni UML veya katman diyagramı**' na tıklayın.

2. **Şablonlar**altında **UML etkinlik diyagramı**' na tıklayın.

3. Diyagrama ad verin.

4. **Modelleme projesine ekle**' de, çözümünüzde mevcut bir modelleme projesi seçin veya **Yeni bir modelleme projesi oluşturun**.

#### <a name="to-draw-elements-on-an-activity-diagram"></a>Etkinlik diyagramında öğeleri çizmek için

1. Araç kutusundan öğeleri diyagram üzerine sürükleyin.

     Ana etkinlikleri diyagrama yerleştirerek, bunları bağlayarak ve ardından ilk ve son düğümler gibi son dokunmaları ekleyerek başlayın.

    > [!NOTE]
    > Varolan öğeleri UML Model Gezgini ' nden diyagram üzerine sürükleyemezsiniz.

2. Öğeleri bağlamak için şu adımları izleyin:

    1. **Etkinlik diyagramı** araç kutusunda **bağlayıcı**' ya tıklayın.

    2. Diyagramda, kaynak öğesine tıklayın.

    3. Hedef öğeye tıklayın.

        > [!NOTE]
        > Bir aracı birden çok kez kullanmak için araç kutusunda araca çift tıklayın.

#### <a name="to-move-an-activity-to-another-package"></a>Bir etkinliği başka bir pakete taşımak için

- **UML Model Gezgini**' nde aktiviteyi bir pakete sürükleyin.

     \- veya-

- **UML Model Gezgini**'nde etkinliğe sağ tıklayın ve **Kes**' e tıklayın. Sonra pakete sağ tıklayıp **Yapıştır**' a tıklayın.

    > [!NOTE]
    > Etkinlik yalnızca ilk öğeyi diyagrama eklediğinizde UML Model Gezgini 'nde görünür.

## <a name="SimpleControlFlow"></a>Denetim akışını açıklama
 Bir etkinlik diyagramı, bir dizi eylem olarak iş sürecini veya yazılım algoritmasını açıklar. Bağlayıcı okları, denetimin bir eylemden sonrakine ardışık olarak nasıl geçtiğini gösterir. Normalde, bir eylem yalnızca önceki eylem tamamlandıktan sonra başlayabilir.

 Aşağıdaki şekilde eylemler, bağlayıcılar, dallar ve döngüler içeren bir dizi eylemi nasıl gösterebileceğinizi gösteren bir örnek verilmiştir. Her öğe aşağıdaki bölümlerde daha ayrıntılı olarak açıklanmıştır.

 ![Basit bir etkinlik diyagramı](../modeling/media/uml-actguidectrl.png "UML_ActGuideCtrl")

 Etkinlik diyagramları, sistem veya uygulamanızı bir eylemden sonrakine göre sıralı bir dizi eylem olarak açıklamanıza yönelik **eylemleri** ve **bağlayıcıları** kullanır.

- Bir Kullanıcı, sistem veya işbirliği içinde her ikisi tarafından gerçekleştirilen her ana görev için bir **eylem** (1) oluşturun.

  > [!NOTE]
  > Yalnızca birkaç eylem ile işleminizi veya algoritmayı açıklamaya çalışın. Çağrı davranışı **eylemlerini** , her bir eylemi, [çağırma davranışı eylemleriyle alt etkinlikleri açıklama](#Subactivities)başlığı altında açıklandığı gibi, ayrı bir diyagramda daha ayrıntılı bir şekilde tanımlamak için kullanabilirsiniz.

- Her bir eylemin başlığının genellikle ne elde aldığını açıkça gösterdiğine emin olun.

- Eylemleri sırasıyla **Bağlayıcılar** (2) ile ilişkilendirin.

- Her eylem, denetim akışındaki bir sonraki eylem başlamadan önce sonlanır. Çakışan eylemleri açıklamak istiyorsanız, [eş zamanlı Akışlar](#Concurrent)bölümünde açıklandığı gibi bir **çatal düğümü** kullanın.

  Diyagramda eylemlerin sırası açıklanmakta olsa da, eylemlerin nasıl yürütüleceğini veya denetimin bir eylemden sonrakine nasıl geçtiğini açıklamaz. Bir iş sürecini temsil etmek için diyagramı kullanırsanız, örneğin bir kişi başka bir e-posta iletisi gönderdiğinde denetim geçirilir. Bir yazılım tasarımını temsil etmek için diyagramı kullanırsanız, denetim bir deyimden diğerine normal yürütme akışı tarafından geçirilebilir.

### <a name="describing-decisions-and-loops"></a>Kararları ve döngüleri açıklama

- Bir kararın sonucunun bir sonraki adımı belirlemesi durumunda olduğunu göstermek için bir **karar düğümü** (3) kullanın. İstediğiniz sayıda giden yol çizebilirsiniz.

- Bir uygulamanın parçasını tanımlamak için etkinlik diyagramı kullanıyorsanız, her bir yol alınması gerektiğinde net olması için koruyucuları (4) tanımlamanız gerekir. Bağlayıcıya sağ tıklayın, **Özellikler**' e tıklayın ve **Özellikler** penceresinde, **Guard** alanı için bir değer yazın.

- Her zaman koruyucuları tanımlamanız gerekmez. Örneğin, bir iş işlemini veya bir etkileşim protokolünü anlatmak için etkinlik diyagramını kullanırsanız, bir dal, kullanıcıya veya etkileşim altındaki bileşenlere açık olan seçenek aralığını tanımlar.

- Bir **karar düğümüne**dallanan iki veya daha fazla alternatif akışı birlikte getirmek Için bir **birleştirme düğümü** (5) kullanın.

    > [!NOTE]
    > Akışları bir eylemde bir araya getirmek yerine, alternatif akışları bir araya getirmek için bir **birleştirme düğümü** kullanmanız gerekir. Bu örnekte, karar düğümünden **menü öğesini seçmek**için doğrudan geri bağlanmak üzere doğru olmaz. Bunun nedeni, denetimin iş parçacıklarının tüm gelen bağlayıcılarına ulaşıp başlamadığı bir işlemdir. Bu nedenle, bir eylemde yalnızca eşzamanlı akışları bir araya getirmeniz gerekir. Daha fazla bilgi için bkz. [eşzamanlı akışlar](#Concurrent).

- Örnekte gösterildiği gibi döngüleri betimleyen dalları kullanın.

    > [!NOTE]
    > Program kodunda olduğu gibi döngüleri iyi yapılandırılmış bir yolla iç içe kullanmayı deneyin. Var olan bir iş sürecini açıkladıysanız, bu, iyileştirmek için bazı fırsatları açığa çıkarmayabilir.

### <a name="starting-the-activity"></a>Etkinlik başlatılıyor
 Etkinlik giriş noktalarını göstermek için iki yol vardır:

- **İlk düğüm**

     Etkinliğin ilk eylemini göstermek için bir **Ilk düğüm** (6) oluşturun.

     Bu yöntem, en çok bir alt etkinliği açıkladığınızda veya etkinliği neyin başlatmamanız gerektiği durumlarda faydalıdır. Örneğin, yemeğin etkinlik sırası bir müşteri bir müşteri tarafından çalıştırıldığında başlar.

- **Olay düğümünü kabul et**

     Bir kullanıcı girişi gibi belirli bir olaya yanıt veren bir iş parçacığının başlangıcını göstermek için, [eşzamanlı akışlar](#Concurrent)bölümünde açıklandığı gibi **kabul etme olay düğümlerini**oluşturun. Düğüme gelen bir akış sağlamatın. Gelen akışın atlanması, olay her gerçekleştiğinde bir iş parçacığının başlatıldığını gösterir.

     Bu yöntem, belirli bir dış olaya yanıt betimleyen en yararlı seçenektir.

### <a name="ending-the-activity"></a>Etkinlik sonlandırılıyor
 Etkinliğin sonunu belirtmek için bir **etkinlik son düğümü** (7) kullanın.

- Bir denetim iş parçacığı bir **etkinlik son düğümüne**ulaştığında, tüm etkinliğin eşzamanlı eylemleri ve alt etkinlikleri sonlandırılır.

- Ek bağlayıcıların dağınıklığını azaltmak için birden fazla etkinlik son düğümünü kullanabilirsiniz.

### <a name="interrupting-the-activity"></a>Etkinliği kesme
 Bir etkinliğin sıradan akışının nasıl kesintiye uğrayabileceğini belirtmek için örneğin, Kullanıcı işlemi iptal etmeye karar verirse, bu olayı dinleyen bir kabul olayı düğümü oluşturabilirsiniz. Daha fazla bilgi için, [eş zamanlı Akışlar](#Concurrent)bölümüne bakın. Bundan sonra bir etkinlik son düğümüne (7) bir denetim akışı oluşturun.

### <a name="swimlanes"></a>Lardır
 Bazen bir etkinliğin eylemlerini, eylemleri gerçekleştiren farklı nesnelere veya iş rollerine karşılık gelen alanlara düzenlemek yararlıdır. Bu alanlarda genel olarak, sütunlar halinde düzenlenir ve *kulvarlar*denir.

- Kulvarları veya diğer alanı çizmek için araç kutusunun **basit şekiller** bölümündeki çizgileri veya dörtgenler kullanın.

- Her bir kulvara etiketlemek için bir açıklama oluşturun ve **saydam** özelliğini **true**olarak ayarlayın.

  Basit şekiller UML modelinin bir parçasını oluşturmuyor ve UML Model Gezgini 'nde görünmez.

## <a name="DataFlows"></a>Veri akışını açıklama
 İki şekilde bir etkinliğin içine ve dışına geçen verileri tanımlayabilirsiniz:

- Bir **nesne düğümü**kullanın. Bu, etkinlikler arasında akan bilgi akışını açıklamanın en basit yöntemidir. Bir nesne düğümü, programdaki bir değişken gibidir. Bir eylemden diğerine geçen bir veya daha fazla değeri depolayan bir şeyi temsil eder.

- Bir **çıkış PIN kodu** ve bir **giriş PIN**'i kullanın. Bu yöntem, bir eylemden çıkışları ve diğer girdileri ayrı olarak açıklamanıza olanak sağlar. PIN 'ler bir programdaki parametrelere benzer. PIN 'ler, nesnelerin girebileceği ve eylem bırakabileceği bağlantı noktalarını temsil eder.

    > [!NOTE]
    > Bu bölümde kullanılan öğelere genel bakış için bkz. [UML etkinlik diyagramları: başvuru](../modeling/uml-activity-diagrams-reference.md).

### <a name="describing-data-flow-with-object-nodes"></a>Nesne düğümleri ile veri akışını açıklama
 Çoğu denetim akışı verileri taşır. Örneğin, "müşteri ayrıntıları sağlar" eyleminden çıkış akışı, Sevkiyat adresine bir başvuru taşır.

 Bu verileri diyagramınızda açıklama eklemek istiyorsanız, bir bağlayıcıyı aşağıdaki şekilde gösterildiği gibi bir nesne düğümü ve iki bağlayıcı ile değiştirebilirsiniz.

 ![Nesne düğümleri, eylemler arasında geçirilen verileri gösterebilir](../modeling/media/uml-actguidedata.png "UML_ActGuideData")

 Mal dağıtımı gibi, gidiş-aşağı dikdörtgenlerin, işlemenin gerçekleştiği eylemleri temsil ettiğini unutmayın. Sevkiyat adresi gibi köşeli çift yönlü dikdörtgenler, bir eylemden diğerine bir nesne akışını temsil eder.

 Nesne düğümüne, düğüm rolünü bir iletken ya da eylemler arasında akan nesnelerin arabelleğini yansıtan bir ad verin.

 Özellikler penceresi nesne düğümünün **türünü** ayarlayabilirsiniz. Tür, tamsayı veya sınıf diyagramında tanımladığınız bir sınıf, arabirim veya sabit listesi gibi bir temel tür olabilir. Örneğin, müşteri adlı başka bir sınıf ile ilişkilendirmede, sokak adresi, şehir vb. öznitelikleri ile birlikte bir sınıf sevkiyat adresi oluşturabilirsiniz. Daha fazla bilgi için bkz. [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md).

> [!NOTE]
> Henüz tanımlanmamış bir türün adını yazarsanız, UML Model Gezgini 'nde **belirtilmeyen türler** altına bir öğe eklenecektir. Daha sonra bir sınıf diyagramında bu adın bir türünü tanımlarsanız, nesne düğümünün türünü yeni türe başvurması için sıfırlamalısınız.

#### <a name="buffering-data-in-object-nodes"></a>Nesne düğümlerinde verileri arabelleğe alma
 Bir nesne düğümü birden çok nesne için bir arabellek işlevi görebilir. Aşağıdaki çizimde, denetim akışı kullanıcının birçok kez [daha fazla Seç] döngüsü (1) içinde gidebildiğini gösterir, ancak seçilen menü öğeleri nesne düğümü (2) Kullanıcı seçimlerini biriktirir. Son olarak, Kullanıcı seçimini tamamladıktan sonra Denetim, seçilen menü öğeleri arabelleğindeki seçimlerin tüm listesini kabul eden Siparişi Onayla eylemine (3) geçer.

 ![Nesne düğümlerinde verileri arabelleğe alma](../modeling/media/uml-actguidebuffer.png "UML_ActGuideBuffer")

 Bir arabellekteki öğelerin, nesne düğümünün özelliklerini ayarlayarak nasıl depolandığını belirtebilirsiniz:

- **Sıralama** özelliğini ayarlayın:

  - Rastgele veya belirtilmemiş bir sıra belirtmek için **sırasız** . (Varsayılan.)

  - Belirli bir anahtara göre bir sipariş belirtmek için **sıralanır** .

  - İlk kez, ilk çıkar sırası belirtmek için **FIFO** .

  - İlk kez geçen bir siparişi belirtmek için **LIFO** .

- **Üst sınır** özelliğini, arabellekte bulunabilecek en fazla nesne sayısını belirtecek şekilde ayarlayın. Varsayılan değer * ' dir. Bu, sınır olmadığı anlamına gelir.

### <a name="describing-data-flow-with-input-and-output-pins"></a>Giriş ve çıkış sabitleyicileri ile veri akışını açıklama
 Bir eylemden çıkışları ve diğer girdileri ayrı olarak anlatmak için bir **çıktı PIN 'i** ve bir **giriş PIN 'i** kullanın.

 ![Giriş ve çıkış sabitleyicileri eylem parametreleridir](../modeling/media/uml-actguidepins.png "UML_ActGuidePins")

 PIN oluşturmak için, araç kutusunda **giriş PIN 'ini** veya **çıkış PIN 'ini** tıklatın ve ardından bir eyleme tıklayın. Sonra, PIN 'i eylemin çevresi etrafında taşıyabilir ve adını değiştirebilirsiniz. **Çağrı davranışı eylemleri**, **işlem eylemleri çağrısı**, **sinyal eylemleri gönderme**ve **olay eylemlerini kabul**etme gibi her türlü eylemde giriş ve çıkış iğneleri oluşturabilirsiniz.

 İki sabitleme arasındaki bir bağlayıcı, bir nesne düğümünden gelen ve giden akışların yaptığı gibi bir nesne akışını temsil eder.

 Her PIN 'e, bir parametre adı gibi ürettiği veya kabul ettiği nesnelerin rolünü gösteren bir ad verin.

 **Tür** özelliğinde aktarılan nesnelerin türünü ayarlayabilirsiniz. Bu, UML sınıf diyagramında oluşturduğunuz bir tür olmalıdır.

 Bağlı PIN 'ler arasında akan nesneler bir şekilde uyumlu olmalıdır. Bunun nedeni, çıkış sabitlemesi tarafından üretilen nesnelerin, giriş pin türünün türetilmiş bir türüne ait olması olabilir.

 Alternatif olarak, nesne akışının, çıktı sabitlemesi türü ve girdi PIN türü arasında veri dönüştüren bir dönüşüm içerdiğini belirtebilirsiniz. Bu türün en yaygın dönüşümü, yalnızca daha büyük bir türden uygun parçayı ayıklar. Şekildeki örnek, sipariş ayrıntısından sevkiyat adresini çıkaran bir dönüşümün varlığını gösterir.

## <a name="Details"></a>Daha ayrıntılı bir eylem tanımlama
 Genellikle yapması gereken sonucu temizlemek için eylemin adını kullanmanın yanı sıra, bir eyleme daha fazla ayrıntı eklemenin bazı yolları aşağıda verilmiştir:

- **Body** özelliğine daha ayrıntılı bir açıklama yazın. Örneğin, program kodunun veya sahte kodun bir parçasını ya da elde edilen sonuçların tüm açıklamasını yazabilirsiniz.

- Eylemi çağrı davranışı eylemiyle değiştirin ve ayrıntılı davranışını ayrı bir etkinlik diyagramı içinde tanıtın. Bkz. [çağrı davranışı eylemleriyle alt etkinlikleri açıklama](#Subactivities).

- Eylemin **yerel yükleme koşullarını** ve **Yerel önkoşulları** özelliklerini, sonucunu daha belirli ayrıntılarla tanımlayacak şekilde ayarlayın. Daha fazla bilgi için bkz. [Postconditions ve önkoşulları tanımlama](#Postcondition).

### <a name="Subactivities"></a>Çağrı davranışı eylemleriyle alt etkinlikleri açıklama
 Bir eylemin ayrıntılı davranışını ayrı bir etkinlik diyagramı kullanarak tanımlayabilirsiniz. Çağrılan davranış, bir çağrı davranışı eylemi tarafından ana etkinlik diyagramınızda temsil edilen bir etkinlik diyagramıdır. Ayrıca, farklı etkinlikler arasında paylaşılan davranışı belirtmek için çağrı davranışı eylemini kullanabilirsiniz, böylece alt etkinliği birden çok kez çizmeniz gerekmez.

 Aşağıdaki şekilde, diyagram 1 çağrı davranışı eylemi olan bir etkinliği gösterir ve diyagram 2 çağrılan davranışı gösteren alt etkinlik diyagramını gösterir.

 ![Ayrı bir etkinlik diyagramı ayrıntılı eylemleri gösterir](../modeling/media/uml-actguidedetail.png "UML_ActGuideDetail")

##### <a name="to-describe-a-sub-activity-with-a-call-behavior-action"></a>Bir çağrı davranışı eylemi ile bir alt etkinliği açıklama

1. Alt etkinliğin diyagramını oluşturmak için, **Çözüm Gezgini**, modelleme projenize sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni öğe**' ye tıklayın.

2. **Yeni öğe Ekle** Iletişim kutusundaki **Şablonlar** altında **etkinlik diyagramı** ' na tıklayın ve **ad** kutusuna, **çağrı davranışınızı**vermek istediğiniz adı yazın.

3. Alt etkinlik için ayrıntılı iş akışını çizin. Bu, çağrılan davranıştır.

    - Çağrılan alt etkinlik diyagramında **Ilk düğüm** , çağrılan davranış çağrıldığında denetimin başladığını gösterir. **Etkinlik son düğümü** , denetimin üst etkinliğe dönmesi gerektiğini gösterir.

4. Çağrılan davranış diyagramına başvuracak şekilde **çağrı davranışı eyleminin** **davranış** özelliğini ayarlayın.

    > [!NOTE]
    > Alt etkinlik diyagramı üzerinde bazı öğeler olmalıdır, aksi durumda diyagram **davranış** özelliği için açılan listede kullanılamaz. Ayrıca, Trident simgesi, **davranış** özelliğini ayarlayıp **çağrı davranışı eylem** şekilinizdeki görünmez.

5. Etkinliğinizin çağrılan etkinliğin tamamlanmasını bekleyip beklemediğini göstermek için eylemin **zaman uyumlu** özelliğini ayarlayın.

    - Değerini **zaman uyumlu** olarak ayarlarsanız, akışın çağrılan etkinlik bitmeden önce bir sonraki eyleme devam edebildiğini siz olduğunu görürsünüz. Eylemden çıkış iğneleri veya giden veri akışları tanımlamanız gerekmez.

### <a name="describing-data-flow-in-and-out-of-sub-activities"></a>Alt etkinliklerin içinde ve dışında veri akışını açıklama
 Yazılım içindeki parametreleri kullandığınız şekilde, alt etkinliklerin içinde ve dışında akan verileri tanımlayabilirsiniz.

- Eylem içine veya dışına akan her veri parçası için çağrılan davranış eyleminde giriş ve çıkış sabitleyicileri (1) oluşturun. Her birini uygun şekilde adlandırın.

- Alt etkinlik diyagramında, çağırma eyleminde her giriş ve çıkış iğnesi için bir **etkinlik parametresi düğümü** (2) oluşturun. Her düğüme karşılık gelen PIN ile aynı adı verin.

  > [!NOTE]
  > Etkinlik parametresi düğümü bir nesne düğümüne benzer. Aradığınız düğüm türünü denetlemek için düğüme sağ tıklayın ve ardından **Özellikler**' e tıklayın. Düğüm türü Özellikler penceresi üst bilgisinde gösterilir.

- Alt etkinlik diyagramında, her etkinlik parametresi düğümünün içine veya dışına nesnelerin akışını gösteren bağlayıcılar çizin.

  ![Çağrı davranışında PIN 'ler etkinlik parametrelerine eşlenir](../modeling/media/uml-actguidesub.png "UML_ActGuideSub")

### <a name="Postcondition"></a>Postconditions ve önkoşulları tanımlama
 Bir eylemin sonucunu ayrıntılı olarak belirtmek için **Yerel Postconditions** ve **Yerel** ön koşullar özelliklerini kullanabilirsiniz. Bu özellikler, efektin nasıl elde edildiğini açıklamadan eylemin etkisini açıklamaktadır.

 Bu özellikleri ayarlamak için eyleme sağ tıklayın ve ardından **Özellikler**' e tıklayın. Değerleri Özellikler penceresi özelliklere yazın.

#### <a name="local-postconditions"></a>Yerel Postconditions
 Sonkoşul, eylemin tamamlandı olarak kabul edilebilmesi için karşılanması gereken bir durumdur. Sırayı Onayla örnek eyleminde, sonkoşulun şu olabilir:

 Müşteri, kredi kartını işlemek için gereken tamamlanmış ve geçerli ayrıntıları sağladı.

 Bir Sonkoşul, eylem meydana gelmeden önce ve sonra durumlar arasında bir ilişki ifade edebilir. Örneğin:

 Faiz oranı, daha önce olmak üzere iki şeydir.

 , Eylemlerde ele aldığınız verilerin belirli özniteliklerine başvurarak daha resmi bir stilde Sonkoşulları yazabilirsiniz. Örneğin:

 `InvoiceTotal == Sum(OrderItem.MenuItem.Price)`

#### <a name="local-preconditions"></a>Yerel Önkoşullar
 Önkoşul, eylem başlamaya hazırlandığında doğru olması gereken bir durumdur. Örneğin, Siparişi Onayla eylemi önkoşula sahip olabilir:

 Müşteri, menüden en az bir öğe seçti.

### <a name="describing-calls-to-operations"></a>Işlemlere çağrıları açıklama
 Genellikle, bir eylem herhangi bir kişi, yazılım veya makine karışımı tarafından gerçekleştirilen işi açıklar. Ancak belirli bir yazılım yöntemi veya işlevine yapılan çağrıyı belirtmek için çağrı Işlemi eylemini kullanabilirsiniz.

- Hangi işlemin çağrıldığını ve hangi nesne veya bileşen üzerinde olduğunu göstermek için çağrı Işlemi eyleminin adını ayarlayın.

- Parametreleri ve dönüş değerlerini belirtmek için çağrı Işlemi eylemine giriş ve çıkış sabitleyicileri ekleyin.

- Etkinliğin işlemin tamamlanmasını bekleyip beklemediğini göstermek için eylemin **zaman uyumlu** özelliğini ayarlayabilirsiniz.

  - Değerini **zaman uyumlu** olarak ayarlarsanız, akışın çağrılan işlem tamamlanmadan önce bir sonraki eyleme devam edebildiğini siz olduğunu görürsünüz. Eylemden çıkış iğneleri veya giden veri akışları tanımlamanız gerekmez.

## <a name="Concurrent"></a>Eş zamanlı Akışlar
 Aynı anda yürütebilecek iki veya daha fazla etkinlik iş parçacığını anlatmak için **çatal düğümünü** ve **JOIN düğümünü** kullanabilirsiniz.

 ![Çatal ve JOIN düğümleri eşzamanlı akışları gösterir](../modeling/media/uml-actguideconcurrent.png "UML_ActGuideConcurrent")

 **Çatalın** (1) etkisi, denetimin iş parçacığını iki veya daha fazla iş parçacığına bölmektir. Önceki eylem sona erdiğinde çatalın çıkış tarafındaki tüm eylemler başlayabilir.

 Bir **JOIN düğümü** (2) eşzamanlı iş parçacıklarını birlikte getirir. **JOIN düğümüne** ait tüm eylemler tamamlanana kadar, **JOIN düğümünden** sonraki eylem başlatılamayabilir.

### <a name="describing-signals-and-events"></a>Sinyalleri ve olayları açıklama
 Bir etkinlikte sinyal gönderme eylemi olarak sinyal gönderen bir işlemde bir adım gösterebilirsiniz. Adımla olay kabul etme eylemi olarak devam etmeden önce belirli bir sinyal veya olay için bekleyen bir adım gösterebilirsiniz.

 Örneğin, bir sipariş gönderen ve daha sonra siparişi bu siparişi gerçekleştirmeden önce alması gereken başka bir adım gösteren bir adım gösterebilirsiniz.

#### <a name="sending-a-signal"></a>Sinyal gönderme
 Bir tür sinyalin veya mesajının diğer etkinliklere veya işlemlere gönderildiğini göstermek için sinyal gönderme eylemi (3) kullanın. Ne tür bir ileti göndereceğini göstermek için eylemin adını kullanın.

- Denetim, varsa Denetim akışında bir sonraki eyleme hemen geçer.

- İşlemin döndürülen tüm bilgilere nasıl yanıt vereceğini göstermek için sinyal gönderme eylemi kullanamazsınız. Bunu yapmak için, ayrı bir olay kabul etme eylemi kullanın.

- Giden iletiyle hangi verilerin gönderilebildiğini göstermek için bir sinyal gönder eylemine gelen veri akışını gösterebilirsiniz. Daha fazla bilgi için bkz. [veri akışını açıklama](#DataFlows).

#### <a name="waiting-for-a-signal-or-event"></a>Sinyal veya olay bekleniyor
 Bu etkinliğin bazı dış olay veya gelen ileti için beklediğini belirtmek için bir kabul olayı eylemi (4) kullanın. İşlemin adını, beklediği olay türünü belirtmek için kullanın.

- Etkinliğinizin akıştaki belirli bir noktada dış bir olay veya ileti bekleyeceğini göstermek için, etkinlik içinde uygun yerde bir gelen Flow olay kabul etme eylemi çizin.

- Etkinliğinizin bir dış olay veya iletiye yanıt verebildiğini göstermek için herhangi bir zamanda bir gelen akış olmadan bir olay kabul etme eylemi çizin. Adlandırılmış dış olay gerçekleştiğinde, etkinlik kabul etme eyleminden başlayarak yeni bir iş parçacığı etkinliğinizden başlatılır.

- Sinyal göndericisine döndürülen bir değeri göstermek için olayı kabul etme eylemi kullanamazsınız. Bu amaç için ayrı bir sinyal gönderme eylemi kullanın.

- Etkinliklerinizin sinyalde alınan verileri nasıl işliyorsa göstermek için, eylemden giden veri akışlarını gösterebilirsiniz. Birden fazla çıkış akışı göstermek istiyorsanız, eylemi kabul et eyleminin **IsUnmarshall** özelliğini ayarlamanız gerekir, bu da eylemin gelen sinyali ayrı bileşenlerine ayrıştırdığını gösterir. Daha fazla bilgi için bkz. [veri akışını açıklama](#DataFlows).

### <a name="describing-multiple-data-flows"></a>Birden çok veri akışını açıklama
 Bir eylemden daha fazla sayıda denetim akışı veya nesne akışı, Eylem sona erdiğinde birden fazla iş parçacığının geldiğini göstermek için çizebilirsiniz. Bu efekt, denetimin ve nesne akışlarının bir karışımını kullanabilmeniz dışında çatala benzer.

 Aşağıdaki örnek, ve eylemlerine kadar birden çok akışı gösterir.

 ![Paralel nesne akışları](../modeling/media/uml-actguidemulti.png "UML_ActGuideMulti")

 "Müşteri ayrıntıları sağlar" eylemi tamamlandığında, iki nesne üretir: "Sevkiyat Adresi" ve "kredi kartı ayrıntıları". İki nesne, farklı eylemlere göre işlenmek üzere ileriye gider.

 Bir eylem, başlamadan önce tüm girişlerinin kullanılabilir olmasını gerektirdiğinden son eylem, kendisine yönelik tüm eylemler tamamlanana kadar başlatılmaz.

### <a name="streams"></a>Akışlar
 Aynı anda yürütülen bir işlem hattını veya bir dizi eylemi açıklamanıza yardımcı olması için bir etkinlik diyagramı kullanabilirsiniz ve verileri sürekli olarak bir eylemden diğerine geçirebilirsiniz.

 Aşağıdaki örnekteki amaç, her eylemin nesneleri üreteve çalışmaya devam edebir işlemdir. Denetim akışı olmadığından, her eylem ilk nesnelerini alır almaz başlayabilir.

 Her birinin bir etkinlik parametre düğümü, nesne düğümü veya giriş ya da çıkış PIN kodu üzerinde en az bir ucu olduğundan, bu örnekteki bağlayıcıların nesne akışları olduğunu unutmayın.

 ![Veri akışı](../modeling/media/uml-actguidestream.png "UML_ActGuideStream")

 1. Örnekte, giriş ve çıkışları temsil eden üç etkinlik parametresi düğümü vardır.

 2. Nesne düğümleri, giriş PIN 'leri ve çıkış sabitleyicileri arabellekleri temsil edebilir. Bir nesne düğümünün üst sınır özelliğini, aynı anda arabellekte kaç tane nesne kullanılabileceğini belirtebilir şekilde ayarlayabilirsiniz.

 3. Bir akışın, farklı Dalların altına doğru bir şekilde bölüşdüğünü göstermek için karar düğümlerini kullanabilirsiniz. Bölme ölçütünün ne olduğunu açıklamak için, düğümlerin açıklamalarını veya unvanlarını kullanabilirsiniz.

 4. Nesnelerin iki veya daha fazla kopyasının olduğunu göstermek için çatal düğümleri kullanabilir, bunları eşzamanlı işleme için gönderebilirsiniz.

 5. Birleştirme düğümlerini, iki işlem akışının bir tane ile birleştirildiğini göstermek için kullanabilirsiniz.

### <a name="selection-and-transformation"></a>Seçim ve dönüştürme
 Bir nesne akışındaki nesnelerin dönüştürüldüğünü, seçili olduğunu veya her ikisini de belirtebilirsiniz. Nesne akışı, bir PIN veya bir nesne düğümüne ait bir akışdır.

- Bir dönüşümde bir akışa giren nesnelerin başka bir türe nasıl dönüştürüleceği açıklanır.

- Seçim, bir akışa giren nesnelerin yalnızca bazılarının alma eylemine nasıl aktarılacağını açıklar.

  Örnek bir dönüşüm gösterir. Diyagramdaki ilk eylem, bir çıktı sabitinde bir posta kodu veya posta kodu oluşturur. Bu, ikinci eylemde bir giriş iğnesine bağlanır. Ancak ikinci eylem tam olarak belirtilen bir adres bekliyor. Bir türden diğerine dönüştürme ikinci bir etkinlikte, adres araması olarak belirtilir. Bu, nesne akışının dönüştürme özelliğinden başvurulur. Adres arama etkinliği, gelen posta kodu için bir etkinlik parametresi düğümü ve giden tam adres için başka bir etkinlik parametresi düğümü içerir.

  ![Nesne dönüşümü başka bir diyagramda tanımlandı](../modeling/media/uml-actguidetransform.png "UML_ActGuideTransform")

  Bir dönüşüm veya seçimi iki şekilde belirtebilirsiniz:

- Giriş veya çıkış sabitlemesine bir açıklama ekleyin.

  - Bu açıklamayı genel bir açıklamadan ayırt etmek için, <\<**dönüştürme**> > veya <\<**seçim**> > ile açıklamayı başlatabilirsiniz.

- Dönüştürmeyi veya seçimi ayrı bir etkinlik diyagramında ayrıntılı olarak belirtin.

  - Bu yöntemi kullanırsanız, dönüştürmenin tanımlandığından okuyucuların açık olmasını sağlamak için bir açıklama ekleyin.

##### <a name="to-specify-a-transformation-or-selection-in-a-separate-activity-diagram"></a>Ayrı bir etkinlik diyagramında bir dönüştürmeyi veya seçimi belirtmek için

1. Dönüşüm veya seçim akışının açıkladığı yeni bir etkinlik diyagramı oluşturun.

   - **Çözüm Gezgini**, projenize sağ tıklayın, **Ekle**' nin üzerine gelin, **Yeni öğe**' ye tıklayın ve ardından **etkinlik diyagramı**' na tıklayın. Diyagrama dönüşüm veya seçim akışı için uygun bir ad verin. **Ekle**'yi tıklatın.

2. Yeni diyagramda:

   1. Biri giriş akışı ve diğeri çıkış için olmak üzere iki etkinlik parametresi düğümü oluşturun.

   2. Nesne akışlarıyla birbirlerine bağlı eylemler oluşturun. Bu, dönüştürmenin veya seçimin nasıl çalıştığını gösterir.

3. Dönüştürmeyi veya seçimi kullanmak istediğiniz diyagramda:

   1. Bir nesne akışı, diğer bir deyişle, bir giriş veya çıkış sabitlemesi, bir nesne düğümü veya etkinlik parametresi düğümü için bir bağlayıcı oluşturun.

   2. Nesne akışına sağ tıklayıp **Özellikler**' e tıklayın.

   3. **Dönüştürme** veya **seçim** özelliğinde, dönüşüm veya seçim akışını belirttiğiniz diyagramı seçin.

   Ayrıca bir nesne düğümü için ve tek tek giriş ve çıkış sabitleyicileri için bir seçim tanımlayabilirsiniz. Bir seçim etkinliğini önceki yordamda olarak tanımlayın ve ardından nesne düğümünün veya giriş ya da çıkış PIN 'inin **seçim** özelliğini ayarlayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md) [UML sıralı diyagramları:](../modeling/uml-sequence-diagrams-reference.md) başvuru UML [Bileşen diyagramları](../modeling/uml-component-diagrams-reference.md) : başvuru UML [kullanım örneği diyagramları:](../modeling/uml-use-case-diagrams-reference.md) başvuru [UML sınıf diyagramları](../modeling/uml-class-diagrams-reference.md) : başvuru UML [Bileşen diyagramları](../modeling/uml-component-diagrams-reference.md) : başvuru [video: etkinlik diyagramlarını kullanarak iş iş akışlarını yakalama](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-4-capture-business-workflows)
