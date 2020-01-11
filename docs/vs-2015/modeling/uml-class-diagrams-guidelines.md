---
title: 'UML sınıf diyagramları: yönergeler | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.logicalclassdiagram.overrideoperationsdialog
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: 94dbfd55-b300-4b49-9049-0831ed849486
caps.latest.revision: 56
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f4fd6eed634da3aea956cddca8d2e1ff6220a94
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850195"
---
# <a name="uml-class-diagrams-guidelines"></a>UML Sınıf Diyagramları: Yönergeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da, veri türlerini ve bunların ilişkilerini ayrı olarak betimleyen *UML sınıf diyagramını* kullanabilirsiniz. Diyagram, sınıfların uygulamaları yerine mantıksal yönlerine odaklanmak için kullanılır.

 Bir UML sınıf diyagramı oluşturmak için **mimari** menüsünde **Yeni UML diyagramı veya katman diyagramı**' nı seçin.

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Bu konu UML sınıf diyagramları hakkındadır. Program kodunu görselleştirmek için oluşturabileceğiniz ve kullanabileceğiniz başka tür bir sınıf diyagramı vardır. Bkz. [sınıfları ve türleri tasarlama ve görüntüleme](https://msdn.microsoft.com/library/ab7aty24.aspx).

## <a name="Using"></a>UML sınıf diyagramlarını kullanma
 Bir UML sınıf diyagramını çeşitli amaçlarla kullanabilirsiniz:

- Bir sistemde kullanılan ve bileşenleri arasında geçirilen türlerin uygulamadan bağımsız açıklamasını sağlamak için.

     Örneğin, Yemek Siparişi türü iş katmanı içinde .NET kodda, bileşenler arasındaki arabirimlerde XML'de, veritabanı içinde SQL'de ve kullanıcı arabirimi içinde HTML'de uygulanabilir. Bu uygulamalar ayrıntıları bakımından farklı olsa da, Yemek Siparişi ile Menü ve Ödeme gibi diğer türler arasındaki ilişki her zaman aynıdır. UML sınıf diyagramı, uygulamalardan ayrı olarak bu ilişkileri tartışmanıza olanak sağlar.

- Uygulama ve kullanıcıları arasında iletişim kurmak ve kullanıcı ihtiyaçlarını açıklamak kullanılan terimlerin sözlüğünü açıklığa kavuşturmak amacıyla. Bkz. [model Kullanıcı gereksinimleri](../modeling/model-user-requirements.md).

     Örneğin, bir restoran uygulamasının kullanıcı öykülerini, kullanım örneklerini veya diğer gereksinim açıklamalarını düşünün. Böyle bir açıklamada; Menü, Sipariş, Öğün, Fiyat, Ödeme ve buna benzer terimleri bulabilirsiniz. Bu terimler arasındaki ilişkileri tanımlayan UML sınıf diyagramı çizebilirsiniz. Bu; gereksinim tanımlamalarında, kullanıcı arabiriminde ve yardım belgelerinde tutarsızlık oluşma riskini azaltacaktır.

### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki
 Bir UML sınıf diyagramı genellikle kullandıkları türlerin açıklamasını sağlamak için diğer modelleme diyagramları ile birlikte çizilir. Her durumda, türlerin fiziksel gösterimi herhangi bir diyagram tarafından kullanılmaz.

 Etkinlik diyagramı

 Bir Nesne Düğümü'nden geçen veri türü.

 Giriş ve çıkış sabitleyicileri ve etkinlik parametresi düğümlerinin türleri.

 Bkz. [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md).

 Sıralı diyagram

 Parametre türleri ve iletilerin dönüş değerleri.

 Yaşam çizgilerinin türleri. Bir yaşam çizgisi sınıfı alabileceği tüm iletiler için işlemler içermelidir.

 Bkz. [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).

 Bileşen diyagramı

 İşlemlerini listeleyen bileşen arabirimleri.

 Bkz. [UML Bileşen diyagramları: yönergeler](../modeling/uml-component-diagrams-guidelines.md).

 Kullanım örneği diyagramı

 Amaçların açıklamalarında ve kullanım örneğinin adımlarında bahsedilen türler.

 Bkz. [UML Kullanım örneği diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="BasicSteps"></a>Sınıf diyagramları çizmek için temel adımlar
 UML sınıf diyagramlarındaki öğeler hakkında başvuru bilgileri için bkz. [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md).

> [!NOTE]
> Modelleme diyagramlarından herhangi birini oluşturmaya yönelik ayrıntılı adımlar [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md)bölümünde açıklanmıştır.

#### <a name="to-create-a-uml-class-diagram"></a>Bir UML Sınıf diyagramı oluşturmak için

1. **Mimari** menüsünde **Yeni UML veya katman diyagramı**' nı seçin.

2. **Şablonlar**altında **UML sınıf diyagramı**' nı seçin.

3. Diyagrama ad verin.

4. **Modelleme projesine ekle**' de çözümünüzde mevcut bir modelleme projesi seçin veya **Yeni bir modelleme projesi oluşturun**ve ardından **Tamam**' ı seçin.

     Yeni bir sınıf diyagramı, **umlclass diyagramı** araç kutusu ile görüntülenir. Araç Kutusu gereken öğeleri ve ilişkileri içerir.

#### <a name="to-draw-a-uml-class-diagram"></a>UML Sınıf Diyagramı çizmek için

1. Bir tür oluşturmak için, araç kutusunda **sınıf**, **arabirim** veya **sabit listesi** aracını seçin ve ardından diyagramın boş bir kısmına tıklayın. (Araç Kutusunu göremiyorsanız, CTRL+ALT+X tuşlarına basın.)

2. Türlere öznitelikler veya işlemler eklemek için, tür içindeki **öznitelikleri**, **işlemleri** veya **DEĞIŞMEZ** değer başlığını seçin ve ENTER tuşuna basın.

     `f(x:Boolean):Integer`gibi bir imza yazabilirsiniz. Bkz. [öznitelikler ve işlemler](#AttributesAndOperations).

     Çeşitli öğeleri hızlıca eklemek için her öğenin sonunda ENTER tuşuna iki kez basın. Listeyi yukarı veya aşağı taşımak için ok tuşlarını kullanabilirsiniz.

3. Bir türü genişletmek veya daraltmak için üst sol köşesindeki köşeli çift ayraç simgesini seçin. Ayrıca bir sınıfın veya arabirimin **öznitelikler** ve **işlemler** bölümünü genişletebilir ve daraltabilirsiniz.

4. Türler arasındaki ilişkilendirmeler, devralma veya bağımlılık bağlantılarını çizmek için uygun araca tıklayın ve ardından kaynak türüne ve hedef türüne tıklayın.

5. Bir pakette tür oluşturmak için, paket aracını kullanarak bir paket oluşturun ve **ardından paket içinde** yeni türler ve paketler oluşturun. Ayrıca, türleri kopyalamak için kopyala komutunu kullanabilir ve onları pakete yapıştırabilirsiniz.

6. Her diyagram, aynı projede diğer diyagramlar arasında paylaşılan modeldeki bir görünümdür. Tüm modelin ağaç görünümünü görmek için **Görünüm**, **diğer pencereler**, **UML Model Gezgini**' ni seçin.

## <a name="UsingTypes"></a>Sınıflar, arabirimler ve numaralandırmalar kullanma
 Araç kutusunda kullanılabilir olan standart üç tür sınıflandırıcı vardır. Bunlar bu belge boyunca *türler* olarak adlandırılır.

 ![Bir sınıf, sabit listesi ve arabirim](../modeling/media/uml-classguidetypes.png "UML_ClassGuideTypes")

- Birçok amaç için veri veya nesne türlerini temsil etmek üzere **sınıfları** (1) kullanın.

- Saf arabirimler ve iç uygulamalar içeren somut sınıflar arasında ayrım yapmanız gereken bir bağlamda **arabirimler** (2) kullanın. Bu fark, diyagramın amacının bir yazılım uygulamasını açıklamak olduğunda yararlıdır. Bu, edilgen veri tanımladığınız zaman veya kullanıcı gereksinimlerini tanımlamak için kavramlar tanımladığınız yerde daha az yararlıdır.

- `Stop` ve `Go`gibi sınırlı sayıda sabit değerli değeri olan bir türü göstermek için bir **sabit listesi** (3) kullanın.

  - Sabit listesine değişmez değerleri ekleyin. Her birine ayrı bir ad verin.

  - İsterseniz her değişmez değer için sayısal bir değer de sağlayabilirsiniz. Sabit listesinin kısayol menüsünü açın, **Özellikler**' i seçin ve ardından **Özellikler** penceresindeki **değer** alanına bir sayı yazın.

  Her türe benzersiz bir ad verin.

### <a name="getting-types-from-other-diagrams"></a>Diğer Diyagramlardan Türleri Alma
 Diğer diyagramdaki türleri UML sınıf diyagramınızda görünür yapabilirsiniz.

 UML Sınıf Diyagramı

 Bir sınıfı birden fazla UML sınıf diyagramında görünür yapabilirsiniz. Tek diyagramda bir sınıf oluşturduğunuzda, sınıfı **UML Model Gezgini** ' nden diğer diyagrama sürükleyin.

 Bu, her diyagramın belirli bir ilişki grubuna odaklanmasını istiyorsanız yararlıdır.

 Örneğin, bir diyagramdaki Yemek Siparişi ve restoran Menüsü arasındaki ilişkilendirmeleri ve diğer diyagramdaki Yemek Siparişi ve Ödeme arasındaki ilişkilendirmeleri gösterebilirsiniz.

 Bileşen Diyagramı

 Bileşen diyagramında bileşenlerde tanımlı arabirimler varsa **UML Model Gezgini** ' nden sınıf diyagramına bir arabirim sürükleyebilirsiniz. Sınıf diyagramında, arabirimin içerdiği yöntemleri tanımlayabilirsiniz.

 Bkz. [UML Bileşen diyagramları: yönergeler](../modeling/uml-component-diagrams-guidelines.md).

 UML Sıralı Diyagramı

 Bir sıralı diyagramda sınıfları ve arabirimleri yaşam çizgilerinden oluşturabilir ve sonra sınıfı **UML Model Gezgini** ' nden UML sınıf diyagramına sürükleyebilirsiniz. Sıralı diyagramdaki her yaşam çizgisi bir nesnenin, bileşenin veya aktörün bir örneğini gösterir.

 Yaşam çizgisinden bir sınıf oluşturmak için, yaşam çizgisi için kısayol menüsünü açın ve **Sınıf Oluştur** veya **Arabirim Oluştur**' u seçin. Bkz. [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).

## <a name="AttributesAndOperations"></a>Öznitelikler ve Işlemler
 Bir öznitelik (4) bir türün her örneğinin sahip olabileceği adlandırılmış değerdir. Bir özniteliğe erişme, örneğin durumunu değiştirmez.

 Bir işlem (5), türün örneklerinin gerçekleştirebildiği bir yöntem veya işlevdir. Bir değer döndürebilir. **IsQuery** özelliği true ise, örneğin durumunu değiştiremez.

 Bir türe öznitelik veya işlem eklemek için, türün kısayol menüsünü açın, **Ekle**' yi seçin ve **öznitelik** veya **işlem**' ı seçin.

 Özelliklerini görmek için öznitelik veya işlemin kısayol menüsünü açın ve ardından **Özellikler**' i seçin. Özellikler **, Özellikler penceresinde görünür** .

 Bir işlemin parametrelerinin özelliklerini görmek için <strong>[...]</strong> seçeneğini belirleyin. **Parametreler** özelliğinde. Yeni özellikler iletişim kutusu görünür.

 Ayarlayabileceğiniz tüm özellikler hakkında ayrıntılı bilgi için bkz.

- [UML sınıf diyagramlarındaki özniteliklerin özellikleri](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [UML sınıf diyagramlarındaki işlemlerin özellikleri](../modeling/properties-of-operations-on-uml-class-diagrams.md)

### <a name="types-of-attributes-and-operations"></a>Öznitelik ve İşlemlerin Türleri
 Her bir öznitelik veya işlem *türü* ve her bir parametre türü aşağıdakilerden biri olabilir:

- **(yok)** -önceki iki nokta (`:`) hariç bırakarak imzada bir türü belirtilmemiş bırakabilirsiniz.

- Standart ilkel türlerden biri: **Boolean**, **Integer**, **String**.

- Modelinizde tanımlı bir tür.

- Şablon türünün parametreli bir değeri, yazılan şablon\<parametresi >. Bkz. [şablon türleri](#Templates).

  Henüz modelinizde tanımlamadığınız bir türün adını da yazabilirsiniz. Ad, UML Model Gezgini 'nde **belirtilmeyen türler** altında listelenecektir.

> [!NOTE]
> Modelinizde o adın sınıfını veya arabirimini daha sonra tanımlarsanız, eski öznitelikler ve işlemler hala Belirtilmemiş Türler'deki öğeye başvuracaktır. Yeni sınıfa başvurmak için onları değiştirmek istiyorsanız, her özniteliği veya işlemi ziyaret etmeli ve aşağı açılan menüden yeni sınıfı seçerek türü sıfırlamalısınız.

#### <a name="multiple-types"></a>Çoklu Türler
 Herhangi bir öznitelik, işlem veya parametre türünün çokluğunu ayarlayabilirsiniz.

 İzin verilen değerler aşağıdaki gibidir:

 `[1]`

 Verilen türden bir değer. Bu varsayılandır.

 `[0..1]`

 **Null** veya verilen türdeki bir değer.

 `[*]`

 Herhangi bir sayıdaki verilen türden örneklerin koleksiyonu.

 `[1..*]`

 Verilen türden en az bir örnekli koleksiyon.

 `[n..m]`

 Verilen türün `n` ve `m` örnekleri arasında bir koleksiyon.

 Çokluk 1'den fazla ise, bu özellikleri de ayarlayabilirsiniz:

- **Issiparişli** -true ise koleksiyonun tanımlı bir sırası vardır.

- **IsUnique** -true ise, koleksiyonda yinelenen değer yok.

### <a name="visibility"></a>Görünürlük
 *Görünürlük* , öznitelik veya işleme sınıf tanımının dışında erişilebilir olup olmadığını gösterir. İzin verilen değerler aşağıdaki gibidir:

 **Public**

 **+**

 Diğer tüm türlerden erişilebilir.

 **Private**

 **-**

 Yalnızca bu türün iç tanımı için erişilebilir.

 **Paket**

 **~**

 Yalnızca bu türü içeren paketin içinde ve onu açıkça içeri aktaran herhangi bir pakette erişilebilir. Bkz. [ad alanlarını ve paketleri tanımlama](#Packages).

 **Protected**

 **#**

 Yalnızca bu tür ve ondan devralınan türler için erişilebilir. Bkz. [Devralma](#Inheritance).

### <a name="setting-the-signature-of-an-attribute-or-an-operation"></a>Bir Özniteliğin veya İşlemin İmzasını Ayarlama
 Bir özniteliğin veya işlemin imzası; onun görünürlüğünü, adını, parametrelerini (işlemler için) ve türünü içeren özellikler koleksiyonudur.

 İmzayı doğrudan diyagramda yazabilirsiniz. Seçmek için özniteliğe veya işleme tıklayın ve ardından ona tekrar tıklayın.

 İmzayı şu biçimde yazın:

```
visibility attribute-name : Type
```

 \- veya -

```
visibility operation-name (parameter1 : Type1, ...) : Type
```

 Örneğin:

```
+ AddItem (item : MenuItem, quantity : Integer) : Boolean
```

 Görünürlüğün kısa biçimini kullanın. Varsayılan değer `+` (genel) ' dir.

 Her tür modelde tanımladığınız türlere, Tamsayı veya Dize gibi standart türlere veya henüz tanımlamadığınız yeni türün adına sahip olabilir.

> [!NOTE]
> Bir parametre listesinde türü içermeyen bir ad yazarsanız, bu parametrenin türü yerine adını gösterir. Bu örnekte, MenuItem ve Tamsayı belirtilmemiş türlere sahip iki parametrenin adı olur:
>
> `AddItem(MenuItem, Integer) /* parameter names, not types! */`

 Bir imzada türün çokluğunu ayarlamak için tür adından sonra köşeli ayraçlar içinde çokluğu yazın, örneğin:

```
+ AddItems (items : MenuItem [1..*])
+ MenuContent : MenuItem [*]
```

 Öznitelik veya işlem statikse, adı imzada altı çizili olarak görünecektir. Soyutsa, ad italik yazı tipinde görünecektir.

 Ancak, **Özellikler** penceresinde yalnızca **static** ve **abstract** özelliklerini ayarlayabilirsiniz.

#### <a name="full-signature"></a>Tam imza
 Özniteliğini veya işlemin imzasını düzenlediğinizde, bazı ek özellikler çizginin sonunda ve her parametreden sonra görünebilir. Küme ayraçları {…} içinde görünürler. Bu özellikleri düzenleyebilir veya ekleyebilirsiniz. Örneğin:

```
+ AddItems (items: MenuItem [1..*] {unique, ordered})
+ GetItems (filter: String) : MenuItem [*] {ordered, query}
```

 Bu özellikler aşağıdaki gibidir:

 `unique`

 **Benzersizdir**

 Koleksiyonda yinelenen değerler yoktur. 1'den büyük çokluktaki türlere uygulanır.

 `ordered`

 **Sıralanmıştır**

 Koleksiyon bir dizidir. False ise, kesin bir ilk öğe yoktur. 1'den büyük çokluktaki türlere uygulanır.

 `query`

 **Sorgu**

 İşlem, örneğinin durumunu değiştirmez. Yalnızca işlemlere uygulanır.

 `/`

 **Türetilir**

 Öznitelik, diğer özniteliklerin veya ilişkilendirmelerin değerlerinden hesaplanır.

 "/" özniteliğin adından önce görünür. Örneğin:

```
/TotalPrice: Integer
```

 Genellikle tam imza, yalnızca siz onu düzenlerken diyagramda görünür. Düzenlemeyi bitirdiğinizde, ek özellikler gizlenir. Tam imzayı her zaman görmek isterseniz, türün kısayol menüsünü açın ve **tam Imzayı göster**' i seçin.

## <a name="Associations"></a>Ilişkilendirmeleri çizme ve kullanma
 Bağlantının yazılımda nasıl uygulandığını dikkate almaksızın, iki öğe arasındaki herhangi bir türden bağlantıyı göstermek için bir ilişkilendirme kullanın. Örneğin; C#'ta işaretçiyi, veritabanındaki ilişkiyi veya XML dosyasının bir bölümünden diğerine yapılan çapraz başvuruyu göstermek için ilişkilendirme kullanabilirsiniz. Gerçek dünyada, dünya ve güneş gibi nesneler arasındaki ilişkilendirmeyi gösterebilir. İlişkilendirme bağlantının nasıl gösterildiğini değil, yalnızca bilginin var olduğunu söyler.

### <a name="properties-of-an-association"></a>Bir İlişkilendirmenin Özellikleri
 Bir ilişkilendirme oluşturduktan sonra, özelliklerini ayarlayın. İlişkilendirme için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

 İlişkilendirmenin bir bütün olarak özelliklerine ek olarak, her bir *rolün*, yani ilişkilendirmenin her bir ucunda kendi özellikleri vardır. Bunları görüntülemek için, **Ilk rol** ve **ikinci rol** özelliklerini genişletin.

 Her rolün bazı özellikleri doğrudan diyagramda görülebilir. Bunlar şu şekildedir:

- Rol adı. Bu, diyagramda ilişkilendirmenin uygun sonunda görünür. Diyagram üzerinde veya **Özellikler** penceresinde bu ayarı yapabilirsiniz.

- Varsayılan değer **1** **' dir**. Bu da diyagramda ilişkilendirmenin uygun sonunun yakınında görünür.

- **Toplama**. Bu, bağlayıcının bir ucunda elmas şeklinde görünür. Bunu, toplama rolündeki örneklerin diğerlerinin örneklerini içerdiğini veya onlara sahip olduğunu göstermek için kullanabilirsiniz.

- **Gezinilebilir**. Yalnızca tek bir rol için true ise, gezinebilir yönde bir ok görünür. Bunu, yazılımda bağlantıların ve veritabanı ilişkilerinin gezinebilirliğini göstermek için kullanabilirsiniz.

  Bu ve diğer özelliklerin tam ayrıntıları için bkz. [UML sınıf diyagramlarındaki Ilişkilerin özellikleri](../modeling/properties-of-associations-on-uml-class-diagrams.md).

### <a name="navigability"></a>Gezinebilirlik
 Bir ilişkilendirme çizdiğinizde, ilişkilendirmenin bir ucunda, ilişkilendirmenin o yönde gezilebilir olduğunu gösteren bir ok olur. Bu, sınıf diyagramınız yazılım sınıflarını ve ilişkilendirmeler işaretçileri veya başvuruları temsil ediyorsa yararlıdır. Ancak varlıkları ve ilişkileri ya da iş kavramlarını göstermek için bir sınıf diyagramı kullandığınızda, gezinebilirliği göstermek pek uygun olmayacaktır. Bu durumda, oklar olmadan ilişkilendirmeler çizmeyi tercih edebilirsiniz. Bu işlemi, ilişkilendirmenin her iki ucunda da **gezinebilir** özelliğini true olarak ayarlayarak yapabilirsiniz.

### <a name="attributes-and-associations"></a>Öznitelikler ve İlişkilendirmeler
 Bir ilişkilendirme, bir özniteliği göstermenin resimsel bir yoludur. Örneğin, Menü türünde bir öznitelik ile Restoran sınıfı oluşturmak yerine, Restoran'dan Menü'ye bir ilişkilendirme çizebilirsiniz.

 Her öznitelik adı bir rol adı olur. Sahip olan türden ilişkilendirmenin karşı ucunda görünür. Örneğin, çizimdeki `myMenu` bakın.

 Genellikle, yalnızca diyagramda çizemeyeceğiniz temel türler gibi türler için öznitelikleri kullanmak daha uygundur.

 ![Eşdeğer ilişkilendirme ve öznitelikler](../modeling/media/uml-classguideattrib.png "UML_ClassGuideAttrib")

## <a name="Inheritance"></a>Devralmayı
 Aşağıdaki ilişkileri oluşturmak için **Devralma** aracını kullanın:

- Özel bir tür ve genel bir tür arasındaki *Genelleştirme* ilişkisi

   \- veya -

- Bir sınıf ve uyguladığı bir arabirim arasındaki *gerçekleştirme* ilişkisi.

  Devralma ilişkilerinde döngüler oluşturamazsınız.

### <a name="generalization"></a>Genelleştirme
 Genelleştirme, özelleştirilmiş veya türetilmiş türün öznitelikleri, işlemleri ve genel veya taban türün ilişkilendirmelerini devralması anlamına gelir.

 Genel tür, ilişkinin ok ucu sonunda görünür.

 Devralınan işlemler ve öznitelikler genellikle özelleştirilmiş türlerde gösterilmez. Ancak, devralınan işlemleri özelleştirilmiş türün işlemler listesine ekleyebilirsiniz. Bu, özelleştirilmiş türdeki işlemlerin bazı özelliklerini geçersiz kılmak veya uygulanan kodun bunu yapmasını göstermek istiyorsanız yararlıdır.

##### <a name="to-override-an-operations-definition-in-a-specializing-type"></a>Özelleştirilmiş türden bir işlemin tanımını geçersiz kılmak için

1. Genelleştirme ilişkisine tıklayın.

    Vurgulu olarak görünür ve yanında bir Eylem etiketi görünür.

2. Eylem etiketine tıklayın ve sonra **Işlemleri geçersiz kıl**' a tıklayın.

    **Geçersiz kılma işlemleri** iletişim kutusu görüntülenir.

3. Özelleştirilmiş tür ' de görünmesini istediğiniz işlemleri seçin ve ardından **Tamam**' a tıklayın.

   Şimdi seçtiğiniz işlemler özelleştirilmiş türde görünür.

### <a name="realization"></a>Gerçekleştirme
 Gerçekleştirme, bir sınıfın arabirim tarafından belirtilen öznitelikler ve işlemleri uygulaması anlamına gelir. Arabirim bağlayıcının ok ucundadır.

 Bir gerçekleştirme bağlayıcısı oluşturduğunuz zaman, arabirim işlemleri otomatik olarak gerçekleştirilmiş sınıfta çoğaltılır. Arabirime yeni işlemler eklerseniz, arabirimin gerçekleştirme sınıflarında çoğaltılırlar.

 Gerçekleştirme ilişkisi oluşturduktan sonra, lolipop gösterimine dönüştürebilirsiniz. İlişkiye sağ tıklayın ve **Lolipop olarak göster**' i seçin.

 Bu, bir sınıfın uyguladığı arabirimleri sınıf diyagramları ile gerçekleştirme bağlantılarını karıştırmadan göstermenize olanak sağlar. Ayrıca ayrı diyagramlarda gerçekleştirdiğiniz arabirim ve sınıfları da gösterebilirsiniz.

 ![Bağlayıcı ve lolipop ile gösterilen gerçekleştirme](../modeling/media/uml-classguiderealize.png "UML_ClassGuideRealize")

## <a name="Templates"></a>Şablon türleri
 Diğer türler veya değerler tarafından parametrelendirilebilen genel veya şablon türü tanımlayabilirsiniz.

 Örneğin, anahtar ve değer türleri tarafından parametrelendirilmiş genel bir Sözlük oluşturabilirsiniz:

 ![İki parametreli şablon sınıfı](../modeling/media/uml-classguidetemplate1.png "UML_ClassGuideTemplate1")

#### <a name="to-create-a-template-type"></a>Bir şablon türü oluşturmak için

1. Bir sınıf veya arabirim oluşturun. Bu, sizin şablon türünüz olacaktır. Uygun şekilde adlandırın, örneğin `Dictionary`.

2. Yeni türün kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

3. **Özellikler** penceresinde, **şablon parametreleri** alanında **[...]** düğmesine tıklayın.

    **Şablon parametresi koleksiyon Düzenleyicisi** iletişim kutusu görüntülenir.

4. Seçin **ekleme**.

5. Şablon türü için Name özelliğini bir parametre adı olarak ayarlayın, örneğin, `Key`.

6. **Parametre türünü**ayarlayın. Varsayılan değer **sınıftır**.

7. Parametresinin yalnızca belirli bir taban sınıfın türetilmiş sınıflarını kabul etmesini istiyorsanız, **kısıtlı değeri** istediğiniz taban sınıfa ayarlayın.

8. İhtiyaç duyduğunuz sayıda parametre ekleyin ve ardından **Tamam**' ı seçin.

9. Diğer sınıflar için yaptığınız gibi öznitelikleri ve işlemleri şablon türüne ekleyin.

     Özniteliği ve işlemlerinin tanımında, türü **Class**, **Interface** veya **Enumeration** olan parametreleri kullanabilirsiniz. Örneğin, `Key` ve `Value`parametre sınıflarını kullanarak bu işlemi `Dictionary`tanımlayabilirsiniz:

     `Get(k : Key) : Value`

     Çeşitliliğini bir çoğulluk içinde bir öğe olarak **tamsayı** olan bir parametre kullanabilirsiniz. Örneğin, bir özniteliğin en büyük tamsayı değeri `[0..max]`olarak bir özniteliğin çoğulluğu tanımlanması için kullanılabilir.

   Şablon türlerini oluşturduğunuz zaman, onları şablon bağlarını tanımlamak için kullanabilirsiniz:

   ![Sözlük şablonundan bağlantılı bir sınıf](../modeling/media/uml-classguidetemplate2.png "UML_ClassGuideTemplate2")

#### <a name="to-use-a-template-type"></a>Bir şablon türü kullanmak için

1. Yeni bir tür oluşturun, örneğin `AddressTable`.

2. Yeni türün kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

3. **Şablon bağlama** özelliğinde, açılan listeden `Dictionary`, örneğin, şablon türünü seçin.

4. **Şablon bağlama** özelliğini genişletin.

     Şablon türünün her parametresi için bir satır görünür.

5. Her parametreyi uygun bir değere ayarlayın. Örneğin, `Key` parametresini `Name`adlı bir sınıfa ayarlayın.

## <a name="Packages"></a>Paketlerle
 Bir UML sınıf diyagramında paketleri görüntüleyebilirsiniz. Bir paket diğer model öğeleri için bir kapsayıcıdır. Bir paket içinde herhangi bir öğe oluşturabilirsiniz. Diyagramda, paketi taşıdığınız zaman paket içindeki öğeler de taşınacaktır.

 Paketin içeriğini gizlemek veya göstermek için daralt/genişlet denetimini kullanabilirsiniz.

 Bkz. [paketleri ve ad alanlarını tanımlama](../modeling/define-packages-and-namespaces.md).

## <a name="generating"></a>UML Sınıf Diyagramlarından Kod oluşturma
 UML sınıf diyagramında sınıfları uygulamaya başlamak için C# kodu oluşturabilir veya kod oluşturma için şablonları özelleştirebilirsiniz. Sağlanan C# şablonlarını kullanarak kod oluşturmaya başlamak için:

- Diyagram veya öğe için kısayol menüsünü açın, **kod oluştur**' u seçin ve ardından gerekli özellikleri ayarlayın.

     Bu özellikleri ayarlama ve belirtilen şablonları özelleştirme hakkında daha fazla bilgi için bkz. [UML Sınıf Diyagramlarından Kod oluşturma](../modeling/generate-code-from-uml-class-diagrams.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [UML modellerini ve diyagramlarını Düzenle](../modeling/edit-uml-models-and-diagrams.md) [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md) [modeli kullanıcı gereksinimleri](../modeling/model-user-requirements.md) [UML Bileşen diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md) [UML sıra diyagramları:](../modeling/uml-sequence-diagrams-reference.md) başvuru UML [kullanım örneği diyagramları](../modeling/uml-use-case-diagrams-reference.md) : başvuru UML [Bileşen diyagramları](../modeling/uml-component-diagrams-reference.md) : başvuru
