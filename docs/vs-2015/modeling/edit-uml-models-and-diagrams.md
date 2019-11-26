---
title: UML modellerini ve diyagramlarını düzenleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.modelingproject
- vs.teamarch.UMLModelExplorer
- vs.teamarch.UMLModelExplorer.rootnode
helpviewer_keywords:
- diagrams - modeling
- UML, copy and paste
- UML, models
- UML model
- UML, element properties
- UML
- UML, diagrams
ms.assetid: 87affd40-8127-4ee9-9d3a-ad977abe2ed6
caps.latest.revision: 86
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 00ac30cc7e9ee3aff0dd64f015a4b4954972c09a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295526"
---
# <a name="edit-uml-models-and-diagrams"></a>UML modellerini ve diyagramları düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birçok farklı diyagram türü tarafından sunulan görünümler aracılığıyla bir UML modeli oluşturabilir ve düzenleyebilirsiniz. Sisteminizde farklı perspektifler sunarak, bu diyagramlar tasarımın ve gereksinimlerinin farklı yönlerini anlamanıza ve tartışmanıza yardımcı olur. Visual Studio, en sık kullanılan UML diyagramı türlerinden beş için şablon sağlar.

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Bu konuda, farklı diyagram türleri arasında ortak olan modeli düzenlemeyle ilgili teknikler açıklanmaktadır. Belirli diyagramlar türlerine özgü daha fazla bilgi için bkz. [uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md).

## <a name="in-this-topic"></a>Bu Konu kapsamında

- [UML diyagramları bir UML modelinin görünümleridir](#Views)

- [UML modelleme diyagramları oluşturma](#Creating)

- [UML modelleme diyagramlarını çizme](#Drawing)

- [Şekilleri ve bağlayıcıları Düzenle](#Editing)

- [Modeldeki değişiklikleri geri alma](#Undo)

- [Diyagramlar arasında öğeleri paylaşma](#Sharing)

- [Öğeleri ve Ilgili öğelerin gruplarını kopyalama](#Copying)

- [Model öğesi veya görünümlerini silme](#Deleting)

- [Diyagramda metin arama](#Searching)

- [Sunu için bir diyagram hazırlama](#presentation)

- [UML tasarımcılarını genişletme](#extensions)

## <a name="Views"></a>UML diyagramları bir UML modelinin görünümleridir
 UML diyagramlarını yalnızca modelleme projelerinde oluşturabilir ve kullanabilirsiniz. Diyagram ve proje oluşturma hakkında daha fazla bilgi için bkz. [UML modelleme projeleri ve diyagramları oluşturma](../modeling/create-uml-modeling-projects-and-diagrams.md).

- Modelleme projesi tek bir UML modeli içerir. Projedeki her UML diyagram, UML modelinin bir görünümüdür.

- Modeli **UML Model Gezgini**'nde görebilirsiniz. **Mimari** menüsünde **Windows**' un üzerine gelin ve **UML Model Gezgini**' ne tıklayın.

- Diyagramdaki her şekil, modeldeki bir öğenin görünümüdür. Bir diyagrama yeni bir şekil yerleştirdiğinizde modelde yeni bir öğe oluşturuyorsunuz.

- Herhangi bir diyagramı kaydettiğinizde, Visual Studio tüm modeli, tüm diyagramlarını ve modelleme proje dosyasını kaydeder.

## <a name="Creating"></a>UML modelleme diyagramları oluşturma

1. Visual Studio 'daki **mimari** menüsünde **Yeni UML veya katman diyagramı**' na tıklayın.

2. Diyagramınızı seçin ve adlandırın.

3. **Modelleme projesine ekle**' de, mevcut bir modelleme projesi seçin veya **Yeni modelleme projesi oluştur**' u seçin.

   > [!NOTE]
   > Modelleme diyagramı, modelleme projesi içinde bulunmalıdır.

   Ayrıca, Çözüm Gezgini var olan bir modelleme projesine diyagram ekleyebilirsiniz. Modelleme projesine sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **Yeni öğe**' ye tıklayın.

#### <a name="to-create-an-empty-uml-modeling-project"></a>Boş bir UML modelleme projesi oluşturmak için

- **Dosya** menüsünde, **Yeni**' nin üzerine gelin, **Proje**' ye tıklayın ve **Yeni proje** iletişim kutusunda **modelleme projeleri**' ne çift tıklayın.

  Modelleme projelerinin nasıl yönetileceği hakkında daha fazla bilgi için bkz. [UML modelleme projeleri ve diyagramları oluşturma](../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="Drawing"></a>UML modelleme diyagramlarını çizme
 Modelleme diyagramı, ilişkilerle bağlantılı model öğelerinin koleksiyonunu görüntüler. Her öğe bir şekil olarak görüntülenir ve her ilişki iki şekil arasında bağlayıcı olarak görüntülenir.

 Biri öğe ve ilişkiler için olmak üzere iki tür araç vardır. Örneğin, UML sınıf diyagramı araç kutusunda **sınıf** bir öğe aracıdır ve **ilişkilendirme** bir ilişki aracıdır.

> [!NOTE]
> Belirli diyagram türlerine özel bilgiler istiyorsanız, bkz. [uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md).

#### <a name="to-create-elements-and-relationships-in-a-uml-modeling-diagram"></a>UML Modelleme diyagramında öğe ve ilişki oluşturmak için

1. Bir model öğesi oluşturmak için, araç kutusunda bir öğe aracına tıklayın ve sonra görünmesini istediğiniz diyagrama tıklayın. Öğesini oluşturduktan sonra, tutamaçlarını sürükleyerek boyutunu ve şeklini ayarlayın.

    Bazı durumlarda, başka bir öğesi içine yeni bir öğe yerleştirebilirsiniz. Örneğin, bir UML sınıf diyagramında bir sınıfı bir paket içine yerleştirebilirsiniz.

   > [!NOTE]
   > Araç kutusunu göremiyorsanız **Görünüm** menüsünde **araç kutusu** ' na tıklayın.

2. Bir ilişki oluşturmak için bir ilişki aracına tıklayın, ilişkinin başlamasını istediğiniz öğeye tıklayın ve sonra sonlandırmak istediğiniz öğeye tıklayın.

    Farklı türde ilişkiler, farklı türlerde öğeler başlatabilir veya bitebilirler. Örneğin, bir UML sınıf diyagramında bir Ilişki ilişkisi bir açıklama öğesinde başlayamaz veya bitemez.

   > [!NOTE]
   > Aynı aracı birkaç kez kullanmak için araca çift tıklayın. İşiniz bittiğinde **işaretçi** aracına tıklayın.

   Bazı tür diyagramlarda basit şekiller de çizebilirsiniz. Bu şekiller modelin bir parçası değildir, ancak bunları diyagramın bölümlerine dikkat çekmek veya farklı alanlara bölmek için kullanabilirsiniz.

## <a name="Editing"></a>Şekilleri ve bağlayıcıları Düzenle
 Bir şekli yeniden boyutlandırdığınızda veya renklendirip bir bağlayıcıyı yeniden yönlendirçalıştığınızda, temel alınan model üzerinde hiçbir etkisi olmaz. Ancak, diyagramda veya UML Model Gezgininde bir şekli yeniden adlandırdığınızda, karşılık gelen öğe UML Model Gezgini 'nde ve bu öğeyi sunan diğer diyagramlarda yeniden adlandırılır.

> [!NOTE]
> Öğe grupları veya kendi seçiminiz olan öğeler oluşturabileceğiniz Yeni araç kutusu öğelerini oluşturmanın basit bir yolu vardır. Daha fazla bilgi için bkz. [Özel Modelleme Araç kutusu öğesi tanımlama](../modeling/define-a-custom-modeling-toolbox-item.md).

 Aşağıdaki şekilde, bir şeklin boyutunun veya adının nasıl değiştirileceği gösterilmektedir.

 ![Model öğesi ayarlama](../modeling/media/uml-drawadjust1.png "UML_DrawAdjust1")

> [!TIP]
> Yerleşik komutlar şekilleri düzgünce hizalamak için bir komut içermez. Ancak, [DIYAGRAMDA UML modeli görüntüleme](../modeling/display-a-uml-model-on-diagrams.md)içindeki örnekteki kodu kopyalayarak kendi hizalama komutunuz kolayca oluşturabilirsiniz.

 Aşağıdaki şekilde, bir bağlayıcının veya etiketlerin yolunun ve konumunun nasıl ayarlanacağı gösterilmektedir.

 ![Bağlayıcıyı ayarlama](../modeling/media/uml-drawadjust2.png "UML_DrawAdjust2")

#### <a name="to-move-one-end-of-a-connector-to-another-shape"></a>Bağlayıcının bir ucunu başka bir şekle taşımak için

1. Aşağıdakilerden birini yapın:

   - **CTRL** tuşuna basın ve bitişi taşıyın.

     \- veya-

   - Bağlayıcıya sağ tıklayın ve ardından **yeniden bağlan**' a tıklayın.

2. Taşımak istediğiniz bağlayıcının sonuna tıklayın.

3. Bağlayıcının taşınmasını istediğiniz şekle tıklayın.

#### <a name="to-change-color-or-other-properties-of-an-element-relationship-or-diagram"></a>Bir öğenin, ilişkinin veya diyagramın rengini veya diğer özelliklerini değiştirmek için

- Öğesine tıklayın ve **Özellikler** penceresindeki alanları ayarlayın.

     **Özellikler** penceresini göremiyorsanız, öğeye sağ tıklayın ve ardından Özellikler ' e tıklayın **.**

#### <a name="to-zoom-in-and-out-on-a-modeling-diagram"></a>Modelleme diyagramında yakınlaştırmak ve uzaklaştırmak için

- Fare tekerleğini döndürürken **CTRL** tuşuna basın ve basılı tutun.

     \- veya-

- **CTRL + SHIFT**tuşlarına basın ve basılı tutun, ardından sol veya sağ fare düğmesine tıklayın.

     \- veya-

- **Mimari tasarımcıları** araç çubuğunda artı işaretine ( **+** ) veya eksi işaretine ( **-** ) tıklayın veya bir yakınlaştırma düzeyi seçin.

## <a name="Searching"></a>Diyagramda arama
 Hızlı Bul işlevi, bir diyagramdaki öğeleri bulur. **Şu görünümü geçerli belgeye**ayarlamanız gerekir **:**

#### <a name="to-search-for-text-in-a-modeling-diagram"></a>Modelleme diyagramında metin aramak için

1. **CTRL + F**tuşlarına basın.

     \- veya-

     **Düzenle** menüsünde **Bul ve Değiştir**' ın üzerine gelin ve **hızlı bul**' a tıklayın.

    > [!NOTE]
    > **Bul ve Değiştir** iletişim kutusunda, **konum** alanını **geçerli belge**olarak ayarlanmış şekilde bırakmanız gerekir. Diğer seçenekler desteklenmez.

2. Bulmak istediğiniz metni yazın ve ardından **Sonrakini Bul**' a tıklayın.

    > [!NOTE]
    > Bulmak istediğiniz metin daraltılmış bir şekil içindeyse, şekil vurgulanacaktır. Şekli genişletin ve sonra **Sonrakini Bul** ' a tıklayın.

## <a name="Undo"></a>Modeldeki değişiklikleri geri alma
 **Düzenleme** menüsündeki **geri al** ve **Yinele** komutlarını kullanarak modelde ve diyagramlarda yaptığınız değişiklikleri geri alabilir ve yineleyebilirsiniz.

 **Her modelleme projesinin tek bir değişiklik yığını vardır.** Modelde ve diyagramlarda yaptığınız tüm değişiklikler bu yığında tutulur. Yığın aynı zamanda bir diyagramdan diğerine odaklanılmış değişiklikler içerir. Undo komutu bu yığındaki değişiklikleri tersine çevirir.

 Örneğin, bu işlemleri gerçekleştirtiğinizi varsayalım: Diyagram1 için bir değişiklik yapın; odağı diyagrama Dönüştür 2; Diagram2 değiştirin. Değişiklikleri geri aldığınızda, ilk geri alma işlemi son değişikliği tersine çevirir; sonraki geri alma odağı diyagrama geri kayacaktır 1; ve üçüncü geri alma değişikliği, diyagram 1 ' de tersine çevirir.

 **Bir diyagramı kapatmak değişiklik yığınını keser.** Bir diyagramı kapatırsanız, bu diyagramda gerçekleştirdiğiniz değişiklikleri geri alamazsınız ve modelde veya diyagramlarından birinde daha önceki değişiklikleri geri alamazsınız.

 **Bir özellik düzenlenirken geri alamazsınız.** Özellikler penceresi bir özelliği veya diyagramdaki bir etiketi düzenlediğinizde, yalnızca bu özellikte yaptığınız değişiklikleri geri alabilirsiniz. ENTER tuşuna basarak özellikte değişiklerinizi doldurun veya ESC tuşuna basarak iptal edin. Daha sonra model ve diyagramlarda yapılan değişiklikleri geri alabilirsiniz.

 **Bir diyagramın kaydedilmeden kapatılması, bekleeceğiniz etkiye sahip olmayabilir.** Bazı değişiklikler yapar ve sonra bir diyagramı kaydetmeden kapatırsanız, değişiklikleriniz yine de modelde korunacaktır. Bunu kaydetmeden yapmak istiyorsanız modelin tamamını kapatmanız önerilir.

## <a name="Sharing"></a>Diyagramlar arasında öğeleri paylaşma
 Bir model öğesinin belirli bir örneğini diyagramlarda birden çok kez görünmesini sağlayabilirsiniz. Bu sınıflar, arabirimler, bileşenler, kullanım örnekleri ve aktörler için geçerlidir.

 Farklı diyagramlarda farklı ilişki gruplarını göstermek istiyorsanız bu yararlı olur. Örneğin, bir diyagramda müşteri ve adres sınıfları arasındaki ilişkilendirmeleri gösterebilirsiniz. Başka bir diyagramda, adres sınıfını posta alanıyla ilişkisi ile yeniden gösterebilirsiniz.

 Herhangi bir diyagramda görünümlerini seçerek veya UML Model Gezgini ' nde seçerek bir model öğesinin, adı gibi özelliklerini değiştirebilirsiniz.

 Her diyagram türü yalnızca bazı model öğesi türlerini gösterebilir. Örneğin, bir bileşen diyagramında kullanım durumunu gösteremezsiniz. Bu nedenle, aşağıdaki yordamlar yalnızca bazı model öğesi ve diyagram birleşimleri için çalışacaktır.

#### <a name="to-add-a-new-view-of-a-model-element-by-using-uml-model-explorer"></a>UML Model Gezgini 'ni kullanarak model öğesinin yeni bir görünümünü eklemek için

1. **UML Model Gezgini**'ni açmak için **mimari** menüsünde **Windows**' un üzerine gelin ve **UML Model Gezgini**' ne tıklayın.

2. Model öğesini **UML Model Gezgini** ' nden aynı projedeki uyumlu bir diyagrama sürükleyin.

     Model öğesinin bir görünümünü sağlayan bir şekil, diğer diyagramlarda veya aynı diyagramda görünümlere ek olarak görünebilir.

    > [!NOTE]
    > Bir sınıf veya bileşeni sıralı diyagram üzerine sürüklediğinizde efekt farklıdır. Bu durumda, türü bu sınıf veya bileşen olan yeni bir yaşam çizgisi oluşturulur. Daha fazla bilgi için bkz. [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).

#### <a name="to-add-a-new-view-of-a-model-element-by-using-paste-reference"></a>Bir model öğesinin yeni bir görünümünü ekleme başvurusunu kullanarak eklemek için

1. Varolan bir öğeye sağ tıklayın ve ardından **Kopyala**' ya tıklayın.

    - Aynı anda birkaç öğeyi kopyalayabilirsiniz. Her bir öğeye tıkladığınızda CTRL tuşunu basılı tutun, bunlardan birine sağ tıklayın ve ardından **Kopyala**' ya tıklayın.

2. Uyumlu bir diyagramın boş bir kısmına sağ tıklayın ve ardından **başvuruyu Yapıştır**' a tıklayın.

     Aynı öğenin başka bir görünümü görüntülenir.

    > [!NOTE]
    > Bu, modelde yeni bir öğe oluşturan **Paste** komutundan farklıdır. Daha fazla bilgi için bkz. [öğeleri ve Ilgili öğelerin gruplarını kopyalama](#Copying).

> [!NOTE]
> Bir ilişki tarafından zaten bağlı olan iki model öğesinin diyagram görünümlerine eklerseniz, ilişkinin bir görünümü diyagramda da görünür. Bu görünümü yalnızca diyagramdan bir öğe kaldırarak veya modelden ilişkiyi silerek silebilirsiniz.

## <a name="Copying"></a>Öğeleri ve Ilgili öğelerin gruplarını kopyalama
 Model öğelerini kopyalayabilir ve yapıştırabilirsiniz ve öğeleri arasındaki ilişkilerle birlikte öğe gruplarını kopyalayabilir ve yapıştırabilirsiniz.

> [!NOTE]
> **Yapıştır** ve **Yapıştır başvuru** komutlarının farklı etkileri vardır. **Paste** , özellikleri kopyalanmış öğeler gibi olan yeni öğeler oluşturur. **Başvuru Yapıştır** , aynı öğelerin yeni görünümlerini oluşturur.

#### <a name="to-copy-elements-and-their-relationships"></a>Öğeleri ve bunların ilişkilerini kopyalamak için

1. Kopyalamak istediğiniz öğelerin bulunduğu diyagramda bir veya daha fazla öğe seçin.

    > [!NOTE]
    > Bir öğe grubunun parçası hariç ilişkiler kopyalayamazsınız.

2. **Düzenle** menüsünde **Kopyala**' ya tıklayın.

3. Öğeleri başka bir diyagrama kopyalamak istiyorsanız yeni diyagramı oluşturun veya var olan diyagramı açın.

4. **Düzenle** menüsünde **Yapıştır**' ı tıklatın.

    - Öğelerin kopyaları, aralarında bağlantı sağlayan ilişkilerin kopyaları ile birlikte görüntülenir.

    - Her yeni öğe, otomatik olarak oluşturulan yeni bir ada sahip olacaktır.

5. Yeni öğe ve ilişkilerin konumlarını, adlarını ve diğer özelliklerini ayarlayın.

> [!NOTE]
> Bir model öğesini bir modelden diğerine kopyalayamazsınız, örneğin aynı çözümde iki modeliniz varsa. Ancak öğeleri bir diyagramdan diğerine kopyalayabilirsiniz.

#### <a name="to-copy-an-entire-diagram"></a>Tüm Diyagramı kopyalamak için

1. Yeni bir diyagram oluşturun.

2. Varolan bir diyagramdaki tüm öğeleri seçin, kopyalayın ve yeni bir diyagrama yapıştırın.

   Çözüm Gezgini kopyalayıp yapıştırarak bir diyagramı çoğaltamaz.

## <a name="Deleting"></a>Model öğesi veya görünümlerini silme
 Bazı tür öğeler, özellikle sınıflandırıcılar, modelden silinmeksizin diyagramdan kaldırılabilir. Sınıflandırıcılar, sınıf diyagramlarında, bileşen diyagramlarında ve kullanım örneği diyagramlarında görüntülenen ana öğelerdir. Birden fazla diyagramda görünebilirler. Bu öğe türleri için iki ayrı komut vardır: **diyagramdan kaldırın** ve **modelden silin**.

 Bunun aksine, diyagramdan bir ilişkiyi sildiğinizde her zaman modelden silersiniz.

> [!NOTE]
> Bir UML diyagramındaki bazı öğe türleri için Etiketler vardır. Etrafında bir dikdörtgen çizerek bu tür öğeleri seçtiğinizde, bu etiketlere sahip öğeleri değil, etiketleri seçmek mümkündür. Bu şekilde seçilen öğelerin bir alt kümesini silmek desteklenmez. Bu öğelerin bir alt kümesini seçmek için, her bir öğeyi tıklatırken **CTRL** tuşuna basın ve basılı tutun.

#### <a name="to-remove-a-classifiers-view-from-a-diagram"></a>Bir sınıflandırıcının görünümünü diyagramdan kaldırma

- Diyagramdaki öğesine sağ tıklayın ve ardından **diyagramdan kaldır**' a tıklayın.

  \- veya-

- Diyagramdaki öğesine tıklayın ve ardından **Delete** tuşuna basın.

  - Öğenin bu görünümü vaniste. Ancak öğe modelde kalır ve **UML Model Gezgini**' nde yine de bulabilirsiniz. Aynı öğenin diğer görünümleri de kalır.

  - Bu şekilde sonlanan her bağlayıcı diyagramdan kaldırılır, ancak gösterdiği ilişki modelde kalır. İlişki altında **UML Model Gezgini** **' ndeki ilişkiyi, bağlandığı**her öğe altında görebilirsiniz.

#### <a name="to-delete-an-element-from-the-model"></a>Modelden bir öğeyi silmek için

- **UML Model Gezgini** ' nde veya bir diyagramda öğeye sağ tıklayın ve ardından **Modelden Sil**' e tıklayın.

  - Öğesi, üzerinde göründüğü her diyagramdan silinir.

  - Bu öğe ile sonlanan her ilişki modelden de silinir.

#### <a name="to-delete-a-relationship-from-the-model"></a>Modelden bir ilişki silmek için

- Diyagramda veya **UML Model Gezgini**' nde ilişkiye sağ tıklayın ve sonra **Modelden Sil**' e tıklayın.

    > [!CAUTION]
    > Bir ilişkiyi modelden kaldırmadan diyagramdan kaldıramazsınız.

     İlişki modelden silinir ve üzerinde göründüğü her diyagramdan silinir.

## <a name="presentation"></a>Sunu için bir diyagram hazırlama
 Aşağıdaki özellikler, diyagramınızın belirli bölümlerine dikkat çekmenize, açıklamalar eklemenize veya bir diyagramı ilgilendiğiniz farklı alanlara böetmenize yardımcı olur.

- Bir diyagramın herhangi bir bölümünü Word, PowerPoint veya başka bir belgeye kopyalayabilirsiniz. İstediğiniz şekilleri ve bağlayıcıları seçin, sağ tıklayın ve ardından **Kopyala**' ya tıklayın.

- Herhangi bir şeklin veya bağlayıcının rengi değiştirilebilir. Bir veya daha fazla şekil seçin ve **Color** özelliğini değiştirin. **Özellikler** penceresini göremiyorsanız **F4**tuşuna basın.

- Bazı türlerdeki diyagramlarda, araç kutusunun **basit şekiller** bölümünden çizgiler, dikdörtgenler ve üç nokta çizebilirsiniz. Bu şekiller UML modelinin bir parçasını oluşturmuyor.

- Bir alanı etiketlemek için, araç kutusundan bir açıklama sürükleyebilir ve sonra **saydam** özelliğini **true**olarak ayarlayabilirsiniz. Basit şekiller gibi, açıklamalar UML modelinin bir parçasını oluşturmuyor ve UML Model Gezgini 'nde görünmez.

- Model öğelerine Not ve açıklama eklemek için, yorum oluşturabilir ve bunları öğelerine bağlayabilirsiniz.

### <a name="to-export-a-diagram-as-an-image"></a>Bir diyagramı görüntü olarak dışarı aktarmak için
 Daha fazla bilgi için bkz. [diyagramları görüntü olarak dışarı aktarma](../modeling/export-diagrams-as-images.md).

## <a name="extensions"></a>UML tasarımcılarını genişletme
 UML araçlarına yeni işlevler ekleyebilir ve diyagram gösterimini kendi gereksinimlerinize uyarlayabilirsiniz. Daha fazla bilgi için bkz. [UML modellerini ve Diyagramları Genişletme](../modeling/extend-uml-models-and-diagrams.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [UML modelleme projeleri ve diyagramları oluşturma](../modeling/create-uml-modeling-projects-and-diagrams.md) [ve modelleme mimarisi](../modeling/analyze-and-model-your-architecture.md) [uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)
