---
title: UML modelleri için standart stereotipler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, stereotypes
- UML diagrams, stereotypes
ms.assetid: 8a8c2321-1cae-4ba8-bb9e-23495c3404d8
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a16c68b3b14be57fb0a6a45c740e5420a82c2ddf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661043"
---
# <a name="standard-stereotypes-for-uml-models"></a>UML modelleri için standart stereotipler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okuyucuya veya makine işlemeye yönelik ek bilgiler sağlamak için UML model öğelerine stereotipler ekleyebilirsiniz. Stereotipler profillerde tanımlanmıştır ve her profil stereotiplerin kümesini sağlar. Visual Studio ile çeşitli profiller sağlanır. Kendi stereotiplerinizi içerebilen kendi profillerinizi de tanımlayabilirsiniz. Daha fazla bilgi için bkz. [UML genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md).

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="the-standard-profiles"></a>Standart profiller
 Aşağıdaki profiller, Visual Studio 'nun desteklenen bir sürümünde, ' i yükledikten hemen sonra kullanılabilir.

|Profil|Amaç|
|-------------|-------------|
|[UML Standart profili L2](#L2)|Bir öğe veya ilişki hakkında ek bilgi eklemek için kullanılabilen, standart bir stereotipler kümesi.|
|[UML Standart profili L3](#L3)|Bir öğe veya ilişki hakkında ek bilgi eklemek için kullanılabilen, standart bir stereotipler kümesi.|
|[C# profili](#NetProfile)|Program kodunu temsil etmek için bir sınıf veya başka bir öğeyi bir UML modelinde düşünüyorsanız, C# profilinden stereotiplerden birini uygulayarak bunu belirtebilirsiniz.<br /><br /> Bu stereotipler Ayrıca model öğelerine özellikler de ekler.|

 Yeni bir UML modeli oluşturduğunuzda, bağlantıları kaldırmadığınız müddetçe L2 ve L3 UML Standart profilleri modele bağlanır.

 Bu profillerin herhangi birinde stereotipleri kullanmak için, önce profili, uygulamak istediğiniz öğeleri içeren bir pakete veya modele bağlamanız gerekir.

#### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Bir profili bir modele veya pakete bağlamak için

1. **UML Model Gezgini**'ni açın. **Mimari** menüsünde **Windows**' un üzerine gelin ve **UML Model Gezgini**' ne tıklayın.

2. Bir paket ya da stereotiplerinizi profilde uygulamak istediğiniz tüm öğeleri içeren bir modeli bulun.

3. Pakete veya modele sağ tıklayın ve ardından **Özellikler**' e tıklayın.

4. **Özellikler** penceresinde, **profiller** özelliğini istediğiniz profiller olarak ayarlayın.

#### <a name="to-remove-the-link-between-a-profile-and-a-model-or-package"></a>Bir profil ile model veya paket arasındaki bağlantıyı kaldırmak için

1. UML Model Gezgini ' nde model veya pakete sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. Özellikler penceresi **profiller** özelliğini boş olarak ayarlayın.

    > [!NOTE]
    > Yalnızca model veya paketteki öğelerin hiçbiri söz konusu profilin stereotiplerini kullanıyorsa, profilin bağlantısını kaldırabilirsiniz.

#### <a name="to-apply-a-stereotype-to-a-model-element"></a>Bir stereotipi model öğesine uygulamak için

1. Diyagramda veya **UML Model Gezgini**' nde model öğesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Stereotipler** özelliğine tıklayın ve uygulamak istediğiniz stereotipleri seçin.

     Seçili stereotipler, çoğu öğe türü için model öğesinde «köşeli ayraç» içinde görünür.

    > [!NOTE]
    > **Stereotipler** özelliğini göremiyorsanız veya istediğiniz stereotip görünmezse, model öğesinin bir paketin içinde veya uygun profilin bağlandığı bir modelin içinde olduğunu doğrulayın.

3. Bazı Stereotipler model öğesi için ek özelliklerin değerlerini ayarlamanıza olanak sağlar. Bu özellikleri görmek için **Stereotipler** özelliğini genişletin.

### <a name="uml-standard-profile-l2"></a><a name="L2"></a> UML Standart profili L2
 Aşağıdaki Stereotipler, profil bağlantısı modelden kaldırılmadığı takdirde UML model öğelerinin anlamını özelleştirmek için kullanılabilir.

 Bu stereotiplerin tam anlamı kendi yerel kurallarınızla ve modeli işlemek için kullanabileceğiniz araçlarla belirlenir.

|Esinin|Şunlara uygulanır|Anlamı|
|----------------|----------------|-------------|
|Aygıt|Sınıf|Genellikle ek mantık uygulayarak başka bir sınıfı destekleyen bir sınıf. Diğer sınıf «Focus» stereotipine sahip olabilir.|
| çağrısı|Bağımlılık|İstemci sınıfı, tedarikçinin işlemlerini çağırır.|
|oluşturmaya|Bağımlılık|İstemci sınıfı, tedarikçinin örneklerini oluşturur.|
|oluşturmaya|İleti|Gönderen alıcıyı oluşturur.|
|oluşturmaya|İşlem|Bu işlem bir Oluşturucu.|
|temiyor|Bağımlılık|İstemci öğesi tamamen veya kısmen tedarikçiden hesaplanır.|
|destroy|İşlem|İşlem örneğini yok eder.|
|belge|Yapıt|Kaynak veya çalıştırılabilir olmayan bir «dosya».|
|varlık|Bileşen|Bileşen bir iş kavramını temsil eder.|
|yürütülür|Yapıt|Yürütülebilir bir «File».|
| dosyası|Yapıt|Fiziksel bir dosya.|
|odak|Sınıf|Birkaç «yardımcı» sınıfı tarafından desteklenen çekirdek iş mantığını tanımlayan bir sınıf.|
|çerçeve|Paket|Bu paket yeniden kullanılabilir bir tasarım modelini tanımlar.|
|uygulamaktır|Bileşen|«Belirtim» uygulamasının uygulanması.|
|ImplementationClass|Sınıf|Sınıfı bir uygulamayı açıklar ve her çalışma zamanı örneği bir sabit uygulama sınıfına sahiptir. «Type» ile karşıtlık.|
|leyebilirsiniz|Bağımlılık|İstemci, tedarikçinin örneklerini oluşturur.|
|kitaplık|Yapıt|Kitaplık «dosya».|
|Metaclass|Sınıf|Bu sınıfın örnekleri de sınıflardır.|
|modelLibrary|Paket|Paketler içeri aktarılarak yeniden kullanılması amaçlanan model öğelerini içerir. Genellikle bir profilin parçası olarak tanımlanır ve profilin uygulamasına göre otomatik olarak içeri aktarılır.|
|process|Bileşen|İşlem tabanlı bir bileşen veya bir iş parçacığı taşıyan bir bileşen.|
|gerçekleştirme|Sınıf, arabirim, bileşen|Bir uygulamayı açıklar.|
|t|Bağımlılık|İstemci sınıfı, bileşeni veya paketi, tedarikçinin belirtim veya tasarımı hakkında daha fazla bilgi sağlar.|
|ğuna|Bağımlılık|Bağımlılığın Tedarikçi sonundaki yorum, istemci sınıfının veya bileşeninin sorumluluklarını tanımlar.|
|betik|Yapıt|Bir yorumtablo «dosya».|
|gönderme|Bağımlılık|Kaynak Işlemi hedef sinyali gönderir.|
|hizmet|Bileşen|Durum bilgisi olmayan bir bileşen.|
|kaynak|Yapıt|Bir derlenebilir «dosya».|
|belirtim|Sınıf, arabirim, bileşen|Bir bileşen ya da nesnenin, dahili olarak nasıl çalıştığını tanımlamadan davranışını tanımlar.|
|sistemin|Bileşen|Büyük bir sistemin parçası. Kullanım örneği diyagramındaki alt sistem, alt sistem stereotipine sahip bir bileşendir.|
|izleme|Bağımlılık|İstemci öğesi, tedarikçiyi sağlayan tasarımın bir parçasıdır. Bu bağımlılığın iki ucu genellikle farklı modellerdir. Bu modellerden biri diğerinin bir gerçekleştirme işlemi olur.|
|tür|Sınıf|Bir nesnenin nasıl uygulandığını bildirmeden davranışını belirtir. Bir nesne, belirtime uygun olduğunda bir türün üyesidir.|
|yardımcı program|Sınıf|Statik işlevler koleksiyonu. Sınıfta örnek yok.|

### <a name="uml-standard-profile-l3"></a><a name="L3"></a> UML Standart profili L3
 Aşağıdaki Stereotipler, profilin modelden bağlantısı kesilmedikçe UML model öğelerinin anlamını özelleştirmek için kullanılabilir.

 Bu stereotiplerin tam anlamı kendi yerel kurallarınızla ve modeli işlemek için kullanabileceğiniz araçlarla belirlenir.

|Esinin|Şunlara uygulanır|Description|
|----------------|----------------|-----------------|
|buildComponent|Bileşen|Bir derlemeyi tanımlamak için kullanılan öğelerin koleksiyonu.|
|metaModel|Modelleme|UML değişkeni veya etki alanına özgü dil gibi bir modelleme dili tanımlar.|
|systemModel|Modelleme|Aynı sisteme uygulanan modellerin koleksiyonu olan bir model (örneğin, bir belirtim, gerçekleştirme ve aralarında izleme ilişkileri).|

## <a name="c-profile"></a><a name="NetProfile"></a> C# profili
 Bu profilde tanımlanan stereotipler, bir model öğesinin program koduna çeviri için tasarlanan olduğunu göstermenizi sağlar. Her stereotip, model öğesinde ayarlayabileceğiniz ek özellikler tanımlar.

 Bu stereotiplerin kullanılabilmesini sağlamak için, bir modeli veya paketi C# profiline bağlayın. Daha sonra stereotiplerinizi bu model veya paketteki model öğelerine uygulayabilirsiniz.

 Kullanılabilir Stereotipler, uygulandıkları öğeler ve kullanılabilir hale yaptıkları ek özellikler aşağıdaki tabloda özetlenmiştir.

|Esinin|Şunlara uygulanır|Özellikler|
|----------------|----------------|----------------|
|**C# sınıfı**|UML sınıfı<br /><br /> Bileşen|**Clr öznitelikleri**<br /><br /> **Is Partial**<br /><br /> **Mühürlü**<br /><br /> **Is Static**<br /><br /> **Is Unsafe**<br /><br /> **Paket görünürlüğü**|
|**C# yapısı**|UML sınıfı<br /><br /> Bileşen|**Clr öznitelikleri**<br /><br /> **Is Partial**<br /><br /> **Is Unsafe**<br /><br /> **Paket görünürlüğü**|
|**C# genel üyeleri**|UML sınıfı<br /><br /> Bileşen|**Clr öznitelikleri**|
|**C# arabirimi**|UML arabirimi|**Clr öznitelikleri**<br /><br /> **Is Partial**<br /><br /> **Paket görünürlüğü**|
|**C# sabit listesi**|UML numaralandırması|**Clrayttributes**<br /><br /> **Temel tür**|
|**C# ad alanı**|UML paketi|**Clr öznitelikleri**<br /><br /> **Taban adı**<br /><br /> **Ad alanlarını kullanma**|

## <a name="see-also"></a>Ayrıca Bkz.
 [UML model öğelerine stereotipler ekleme](../modeling/add-stereotypes-to-uml-model-elements.md) [modellerinizi profiller ve STEREOTIPLER ile özelleştirme](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [UML genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md)
