---
title: Paketleri ve ad alanlarını tanımlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, namespaces
- UML, namespaces
- UML, packages
- UML model, packages
ms.assetid: 79147068-02d5-4b70-933d-f647c1da3829
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 657bb91295134352fb00649ad06f59e34593c578
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669911"
---
# <a name="define-packages-and-namespaces"></a>Paketleri ve ad alanlarını tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da, bir *paket* sınıflar, kullanım örnekleri ve BILEŞENLER gibi UML öğelerinin tanımları için bir kapsayıcıdır. Bir paket, diğer paketleri de içerebilir.

 UML Model Gezgini 'nde, bir paket içindeki tüm tanımlar paketin altında iç içe yerleşmekte. UML modeli bir tür pakettir ve ağacın kökünü oluşturur.

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-topic"></a>Bu Konu kapsamında
 [Ad alanları](#Namespaces)

 [Paketleri oluşturma ve görüntüleme](#Packages)

 [Paketler içinde model öğeleri oluşturma](#Elements)

 [Öğeleri bir paketin içine veya dışına taşıma](#Moving)

 [Öğeleri bir pakete yapıştırma](#Pasting)

 [Paketler arasındaki Ilişkileri içeri aktarma](#Import)

 [Bir ad alanından diğerine başvurular](#References)

 [Paketlerin özellikleri](#Properties)

## <a name="namespaces"></a><a name="Namespaces"></a> Öznitelikleri
 Paketler, çalışmayı farklı alanlara ayırmak için faydalıdır. Her paket, farklı paketlerde tanımlanmış adların birbirleriyle çakışmaması için bir ad alanı tanımlar.

 Her öğenin tam ad özelliği, ait olduğu paketin tam adı ve öğenin kendi adı gelir. Örneğin, paketiniz çağrılırsa `MyPackage` , paket içindeki bir sınıf gibi nitelikli bir ada sahip olur `MyPackage::MyClass` . Her öğe bir model içinde bulunduğundan, her nitelikli ad modelin adıyla başlar.

 Model ayrıca bir ad alanını tanımlar, böylece bir modeldeki her öğenin tam adı modelin adıyla başlar.

 Diğer model öğeleri de ad alanlarını tanımlar. Örneğin, bir işlem kendi üst sınıfı tarafından tanımlanan ad alanına ait olduğundan, tam adı benzer olur `MyModel ::MyPackage ::MyClass ::MyOperation` . Aynı şekilde, bir eylem, üst etkinliği tarafından tanımlanan ad alanına aittir.

 Paketler kapsayıcılardır. Bir paketi taşırsanız veya silerseniz, sınıflar, paketler ve içinde tanımlanan diğer şeyler da taşınır veya silinir. Aynı, ad alanlarını tanımlayan diğer öğelerin aynısını de doğrudur.

## <a name="creating-and-viewing-packages"></a><a name="Packages"></a> Paketleri oluşturma ve görüntüleme
 Bir UML sınıf diyagramında veya UML Model Gezgini ' nde bir paket oluşturabilirsiniz.

#### <a name="to-create-a-package-in-a-uml-class-diagram"></a>UML sınıf diyagramında bir paket oluşturmak için

1. Bir UML sınıf diyagramı açın veya yeni bir tane oluşturun.

2. **Paket** aracına tıklayın.

3. Diyagramda herhangi bir yere tıklayın. Yeni bir paket şekli görüntülenir.

     Bir paketi diğerine iç içe yerleştirmek için mevcut bir paketin içine tıklayabilirsiniz.

4. Paket için yeni bir ad yazın.

#### <a name="to-create-a-package-in-uml-model-explorer"></a>UML Model Gezgini 'nde bir paket oluşturmak için

1. **UML Model Gezgini**'ni açın. **Mimari** menüsünde **Windows**' un üzerine gelin ve **UML Model Gezgini**' ne tıklayın.

2. Yeni bir paket eklemek istediğiniz bir pakete veya modele sağ tıklayın.

   > [!NOTE]
   > Bir paketi başka bir paket içinde iç içe geçirebilirsiniz.

3. **Ekle** ' nin üzerine gelin ve ardından **paket**' e tıklayın.

    Modelde yeni bir paket görüntülenir.

4. Paket için yeni bir ad yazın.

   UML Model Gezgini 'nde bir paket oluşturduysanız, bunu UML sınıf diyagramında görüntüleyebilirsiniz. Bir paketi birden fazla UML sınıf diyagramında da görüntüleyebilirsiniz.

#### <a name="to-show-an-existing-package-on-a-uml-class-diagram"></a>Bir UML sınıf diyagramında var olan bir paketi göstermek için

- Paketi UML Model Gezgini ' nden sınıf diyagramı üzerine sürükleyin.

    > [!NOTE]
    > Bu, paketin bu diyagramda bir görünümünü oluşturur. Paketin içerdiği tüm öğeleri göstermesi gerekmez. Bir paketin tüm içeriğini gördiğinizden emin olmak için UML Model Gezgini ' nde görüntüleyin.

## <a name="creating-model-elements-inside-packages"></a><a name="Elements"></a> Paketler içinde model öğeleri oluşturma
 Model öğelerini bir paketin içine yerleştirebileceğiniz dört yol vardır:

- UML Model Gezgini 'nde bir pakete yeni bir öğe ekleyin.

- UML sınıf diyagramı 'ndaki paketlere sınıflar ve diğer türler ekleyin.

- Diyagramda oluşturulan yeni öğelerin belirttiğiniz paketin içine yerleştirilmesi için bir diyagramın **LinkedPackage** özelliğini ayarlayın. Sınıf diyagramları, Bileşen diyagramları ve kullanım örneği diyagramları bu şekilde bir pakete bağlanabilir.

- Öğeleri UML Model Gezgini 'nde bir paketin içine veya dışına taşıyın.

  Paketteki bir öğe, UML Model Gezgini 'nde paketin altında görünür ve tam adı paketin tam adıyla başlar. Herhangi bir öğenin tam adını görmek için, öğeye sağ tıklayın ve ardından **Özellikler**' e tıklayın. **Nitelenmiş ad** özelliği **Özellikler** penceresinde görünür.

#### <a name="to-create-an-element-in-a-package-in-uml-model-explorer"></a>UML Model Gezgini 'nde bir pakette öğe oluşturmak için

1. **UML Model Gezgini**'ni açın. **Görünüm** menüsünde **diğer pencereler**' ın üzerine gelin ve **UML Model Gezgini**' ne tıklayın.

2. Yeni bir öğe eklemek istediğiniz bir pakete veya modele sağ tıklayın.

3. **Ekle**' nin üzerine gelin ve sonra eklemek istediğiniz öğe türüne tıklayın.

     Yeni öğe paketin altında görünür.

4. Yeni öğe için bir ad yazın.

    > [!NOTE]
    > Yeni öğe hiçbir diyagramda görünmüyor. Yeni öğenin bir görünümünü oluşturmak için UML Model Gezgini 'nden diyagram üzerine sürükleyebilirsiniz. Diyagram bu tür bir öğeyi görüntüleyecek bir tür olmalıdır.

#### <a name="to-create-an-element-in-a-package-on-a-uml-class-diagram"></a>UML sınıf diyagramında bir pakette öğe oluşturmak için

1. Üzerinde paketin göründüğü bir sınıf diyagramını açın.

    - Bunu henüz yapmadıysanız yeni bir paket oluşturun.

    - Varolan bir paketi bir sınıf diyagramında görünmesini sağlamak için, paketi **UML Model Gezgini** ' nden sınıf diyagramına sürükleyebilirsiniz.

2. Bir sınıf, arabirim veya sabit listesi veya paket için araca tıklayın.

3. Yeni öğeyi yerleştirmek istediğiniz pakete tıklayın.

     Yeni öğe paketin içinde görüntülenir.

#### <a name="to-create-all-the-elements-of-a-diagram-in-a-specified-package"></a>Belirtilen pakette bir diyagramın tüm öğelerini oluşturmak için

1. Bunu yapmadıysanız, paketi oluşturun.

2. Bileşen diyagramı, kullanım durumu diyagramı veya UML sınıf diyagramı açın.

3. Diyagramın özelliklerini açın. Diyagramın boş bir kısmına sağ tıklayıp **Özellikler**' e tıklayın.

4. **Bağlı paket** özelliğinde, diyagramın içeriğini içermesini istediğiniz paketi seçin.

5. Diyagramda yeni öğeler oluşturun. Bunlar pakete yerleştirilir.

    - Her öğenin **tam adı** paketin tam adıyla başlayacaktır.

    - **UML Model Gezgini**' nde her öğe paketin altında görünür.

## <a name="moving-elements-into-and-out-of-packages"></a><a name="Moving"></a> Öğeleri paketlerin içine ve dışına taşıma
 Bir veya daha fazla öğeyi bir paketin içine veya dışına taşıyabilirsiniz.

 Bir paketi taşırsanız, içindeki her şey onunla birlikte taşınır.

#### <a name="to-move-an-element-into-or-out-of-a-package"></a>Bir öğeyi bir paketin içine veya dışına taşımak için

- UML Model Gezgini ' nde, öğesini kökü paket olan ağacın içine veya dışına sürükleyin.

     Öğenin tam adı, yeni sahip olduğu paketi veya modeli gösterecek şekilde değişir.

     \- veya

- Bir sınıf diyagramında, öğeyi bir paket şekline sürükleyin.

     Öğenin tam adı, yeni sahip olduğu paketini gösterecek şekilde değişir.

    > [!NOTE]
    > Bir öğeyi bir paketin dışına diyagramın boş bir kısmına sürüklerseniz, sahibi olan paket değişmez. Bu, paketlerin kendilerini göstermek zorunda kalmadan çeşitli paketlerin öğelerini gösteren bir diyagram yapmanızı sağlar.

## <a name="pasting-elements-into-a-package"></a><a name="Pasting"></a> Öğeleri bir pakete yapıştırma
 Bir öğeyi pakete yapıştırabilirsiniz. Bir ilgili öğe grubunu bir pakete yapıştırırsanız, aralarındaki ilişkiler de yapıştırılacak.

#### <a name="to-paste-elements-into-a-package-on-a-uml-class-diagram"></a>UML sınıf diyagramı 'ndaki bir pakete öğe yapıştırmak için

1. UML sınıf diyagramında, kopyalamak istediğiniz tüm öğeleri seçin. Bunlardan birine sağ tıklayın ve ardından **Kopyala**' ya tıklayın.

2. Pakete sağ tıklayın ve ardından **Yapıştır**' a tıklayın.

    > [!NOTE]
    > Paket farklı bir diyagramda olabilir.

## <a name="import-relationships-between-packages"></a><a name="Import"></a> Paketler arasındaki Ilişkileri içeri aktarma
 **İçeri** aktarma aracını kullanarak paketler arasında bir içeri aktarma ilişkisi tanımlayabilirsiniz.

 İçeri aktarma, içeri aktarılan pakette tanımlanan ve ilişkinin ok sonundaki öğeler olan öğelerin içeri aktarma paketinde etkin bir şekilde tanımlandığı anlamına gelir. Görünürlüğü **paket** olarak tanımlanan tüm öğeler içeri aktarma paketinde de görünür olacaktır.

 İçeri aktarma ilişkilerinde döngüler oluşturmaktan kaçının.

## <a name="references-from-one-namespace-to-another"></a><a name="References"></a> Bir ad alanından diğerine başvurular
 Bir paketin başka bir öğesine bir öğesine başvurmak istiyorsanız, öğenin tam adını kullanmanız gerekir.

 Örneğin, paketin `SalesCommon` türü tanımlıyor olduğunu varsayalım `CustomerAddress` . Başka bir pakette, `RestaurantSales` `MealOrder` Müşteri adresi türünde bir özniteliğe sahip bir tür tanımlamak istiyorsunuz. İki seçeneğiniz vardır:

- Tam nitelikli adı kullanarak özniteliğin türünü belirtin `SalesCommon::CustomerAddress` . Bunu yalnızca `CustomerAddress` **görünürlük** özelliği **ortak**olarak ayarlandıysa yapmanız gerekir.

- Paketten pakete bir Içeri aktarma ilişkisi oluşturun `RestaurantSales` `SalesCommon` . Daha sonra `CustomerAddress` tam adını kullanmadan kullanabilirsiniz.

## <a name="properties-of-packages"></a><a name="Properties"></a> Paketlerin özellikleri
 Her paket aşağıdaki özelliklere sahiptir. Özellikleri görmek için, bir diyagramda veya UML Model Gezgini ' nde pakete sağ tıklayın ve ardından **Özellikler**' e tıklayın.

|Özellik|Varsayılan değer|Açıklama|
|--------------|-------------------|-----------------|
|**Ad**|(yeni bir ad)|Paket adı. Diyagramda veya Özellikler penceresi değiştirebilirsiniz.|
|**Tam ad**|*Container* :: *Package adı*|Tam ad, bu paketi içeren paketin veya modelin adı. Daha fazla bilgi için bkz. [ad alanları](#Namespaces).|
|**Profiller**|olmamalıdır|Bu pakete bağlı profillerin listesi. Bu profiller, paket içindeki öğelere uygulanabilen stereotipler sağlar. Daha fazla bilgi için bkz. [modelinize profiller ve Stereotipler Ile özelleştirme](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|
|**Görünürlük**|**Geneldir**|Paketin üst paketinin dışında görünürlüğü.|
|**İş öğeleri**|olmamalıdır|Bağlantılı iş öğelerinin listesi. Daha fazla bilgi için bkz. [model öğelerini ve iş öğelerini bağlama](../modeling/link-model-elements-and-work-items.md).|
|**Tanım konumu**|(bir ad)|Paketin ayrıntılarının depolandığı dosya adı. Dosyalar **ModelDefinition** proje klasörünün içindedir. Bu bilgiler, kaynak denetimi amacıyla yararlı olabilir.|
|**Açıklama**|olmamalıdır|Paketin açıklaması.|
|**Kliş**|olmamalıdır|Bu pakete uygulanan stereotipler. Kullanılabilir stereotiplerin listesi, bu paket için seçtiğiniz profiller ve onu içeren paketler tarafından belirlenir. Daha fazla bilgi için bkz. [modelinize profiller ve Stereotipler Ile özelleştirme](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|

## <a name="how-packages-are-stored"></a>Paketler nasıl depolanır
 Yeni bir paket oluşturduğunuzda, **ModelDefinition** proje klasöründe yeni bir **. UML** dosyası oluşturulur. Aynı zamanda bir paket olan kök modeli bir **. UML** dosyasında da depolanır.

 Ayrıca, her diyagram, diyagramın şekillerini temsil eden biri ve şekillerin konumlarını kaydeden bir **. Layout** dosyası olmak üzere iki dosyada depolanır.

## <a name="see-also"></a>Ayrıca Bkz.
 [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md) [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md) [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md) [sürüm denetimi altındaki modelleri ve diyagramları yönetme](../modeling/manage-models-and-diagrams-under-version-control.md)
