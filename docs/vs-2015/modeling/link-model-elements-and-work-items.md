---
title: Model öğelerini ve iş öğelerini bağlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.common.removeworkitemsdialog
- vs.teamarch.common.linkworkitemsdialog
helpviewer_keywords:
- UML - extending, linking to TFS work items
- UML - extending, linking work items
- work items, creating from UML models
- UML model, creating work items
- work items, linking to UML models
- UML model, linking work items
ms.assetid: e687a490-0f93-412c-a1ff-eea83cf7ba07
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ee4fea9e3fb1d5b4d27b1d520ac2ab036747f73d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657624"
---
# <a name="link-model-elements-and-work-items"></a>Model öğelerini ve iş öğelerini bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da model öğelerini ve Team Foundation Server veya Visual Studio Team Services iş öğelerini bağlayarak modelinizle ilgili görevleri, test çalışmalarını, hataları, gereksinimleri, sorunları ve diğer işleri izleyin. Bağlantılı iş öğelerini model öğeleriyle ilişkilendirmek bunlara belgeler ekleyin.

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Bağlantı oluşturmak ve açmak için Takım Gezgini kullanmanız gerekir. Modelleme projenizin ve diyagramlarınızın, başkalarının bağlantılı diyagramları açamaması için sürüm denetimine iade edildiğinden emin olun.

 Örneğin, şunları bağlayabilirsiniz:

- Hikayenin sıralı işlemler olarak nasıl gerçekleştiğini açıklayan kullanıcı hikayesi iş öğesi ve etkinlik diyagramı

- Kullanım durumunun doğru bir şekilde uygulandığından emin olmanızı sağlayan, kullanım durumu ve test çalışması iş öğelerindeki bir kullanım durumu

- Özniteliğin uygulanmasında bir hata gösteren UML sınıf diyagramındaki ve hata iş öğesindeki bir öznitelik

- Bileşenin gelişimini izleyen bileşen diyagramındaki ve görev iş öğesindeki bir bileşen. Böyle bir görev genellikle daha küçük görevlere ayrılır

  İş öğelerini, şu öğelerde olduğu gibi modelleme diyagramlarında veya UML Model Gezgini'nde seçebileceğiz herhangi bir öğeye bağlayabilirsiniz:

- UML modellerindeki UML sınıfları, yaşam çizgileri, kullanım durumları, alt sistemler, etkinlikler, nesne düğümleri, bileşenler, arabirimler gibi tüm öğeler

- UML modellerindeki ilişkilendirme, genelleştirme, bağımlılık, akış ve iletiler gibi tüm ilişkiler

- Sınıfların öznitelikleri ve işlemleri, yaşam çizgilerinin yürütme örnekleri, etkinliklerin giriş ve çıkış bağlantı noktaları, bileşenlerin parça ve bağlantı noktaları gibi öğelerin parçaları

- Katmanlar ve katman bağımlılıkları

- Açıklamalar ve açıklama bağlantıları

- Diyagramlar. Bir diyagram seçmek için diyagramın boş bir kısmını seçin.

> [!WARNING]
> Bir iş öğesi oluşturmak veya bu öğeye bağlanmak için TFS kaynak kodu denetimine (SCC) zaten bağlanmış olmanız gerekir. Farklı bir TFS SCC bağlantısını açmaya çalışırsanız, Visual Studio geçerli çözümü otomatik olarak kapatır. Bir iş öğesini oluşturmayı veya bir iş öğesini bağlamayı denemeden önce uygun SCC 'e zaten bağlı olduğunuzdan emin olun. Visual Studio 'nun sonraki sürümlerinde, bir SCC 'e bağlı değilseniz menü komutları kullanılamaz.

- [Takım Projesine Bağlan](#ConnectTFS)

- [Model öğesini yeni bir iş öğesine bağlama](#LinkNew)

- [Model öğesini var olan bir iş öğesine bağlama](#LinkExisting)

- [Model öğesine bağlı iş öğelerini görüntüle](#OpenWorkItem)

- [İş öğesine bağlı model öğelerini görüntüle](#ViewLinkedModels)

- [Model öğeleri ve iş öğeleri arasındaki bağlantıları sil](#RemoveLinks)

- [Sorun giderme](#Troubleshooting)

## <a name="ConnectTFS"></a>Takım Projesine Bağlan
 Bağlantı oluşturmak, görüntülemek veya kaldırmak için öncelikle takım projenize bağlanmanız gerekir.

1. **Takım** menüsünde, Takım Gezgini penceresini göstermek Için **Bağlantıları Yönet** ' i seçin.

2. Doğru proje görünmüyorsa, Takım Gezgini ' de **Bağlantıları Yönet** ' i seçin ve sonra **Takım Projesine Bağlan**' ı seçin. Ardından gerekirse doğru projeleri veya sunucuyu seçin.

3. **Takım Gezgini**, iş öğelerini oluşturmak, bağlamak veya görüntülemek istediğiniz projeyi seçin.

## <a name="LinkNew"></a>Model öğesini yeni bir iş öğesine bağlama

1. Kullanmak istediğiniz TFS örneğine bağlandığınızdan emin olun.

2. Modelleme diyagramında veya **UML Model Gezgini**' nde, model öğesinin kısayol menüsünü açın.

3. Oluşturmak istediğiniz **iş** öğesi ve iş öğesi türünü seçin.

4. İş öğesi formunda alanları doldurun. **Iş öğesini kaydet**' i seçin.

     Visual Studio model öğesini yeni iş öğesine bağlar. Simge model öğesi üzerinde veya yakınında görünür.

> [!WARNING]
> Bir iş öğesi oluşturmak veya bu öğeye bağlanmak için TFS kaynak kodu denetimine (SCC) zaten bağlanmış olmanız gerekir. Farklı bir TFS SCC bağlantısını açmaya çalışırsanız, Visual Studio geçerli çözümü otomatik olarak kapatır. Bir iş öğesini oluşturmayı veya bir iş öğesini bağlamayı denemeden önce uygun SCC 'e zaten bağlı olduğunuzdan emin olun. Visual Studio 'nun sonraki sürümlerinde, bir SCC 'e bağlı değilseniz menü komutları kullanılamaz.

## <a name="LinkExisting"></a>Model öğesini var olan bir iş öğesine bağlama
 Model öğelerini iş öğelerine bağladığınızda, iş öğesinden değil, model öğesinden başlayın.

1. Kullanmak istediğiniz TFS örneğine bağlandığınızdan emin olun.

2. Modelleme diyagramında veya **UML Model Gezgini**' nde, model öğesinin kısayol menüsünü açın. **Iş öğesine bağla**' yı seçin. Ardından **Proje** alanından projenizi seçin.

3. Aşağıdaki adımlardan birini uygulayarak bir veya daha çok iş öğesini model öğesine bağlamak için seçin:

    - **Kaydedilmiş sorguda**bir sorgu seçin.

    - Bir veya daha fazla iş öğesinin kimliklerini boşluklarla ayırarak, **kimlik**olarak yazın.

    - **Başlık içeren**bir sözcük veya tümcecik yazın.

4. **Bul**' ı seçin.

5. İş öğesi listesinde, iş öğesi veya bağlamak istediğiniz iş öğelerini seçin.

     İşiniz bittiğinde, model öğesinin **Iş öğeleri** özelliği öncekinden daha büyük bir sayı gösterir. Simge model öğesi üzerinde veya yakınında da görünür.

> [!WARNING]
> Bir iş öğesi oluşturmak veya bu öğeye bağlanmak için TFS kaynak kodu denetimine (SCC) zaten bağlanmış olmanız gerekir. Farklı bir TFS SCC bağlantısını açmaya çalışırsanız, Visual Studio geçerli çözümü otomatik olarak kapatır. Bir iş öğesini oluşturmayı veya bir iş öğesini bağlamayı denemeden önce uygun SCC 'e zaten bağlı olduğunuzdan emin olun. Visual Studio 'nun sonraki sürümlerinde, bir SCC 'e bağlı değilseniz menü komutları kullanılamaz.

## <a name="OpenWorkItem"></a>Model öğesine bağlı iş öğelerini görüntüle

1. **Takım Gezgini**, iş öğelerinin model öğesiyle bağlantılı olduğu takım projesine bağlı olduğunuzdan emin olun.

2. Modelleme diyagramında veya **UML Model Gezgini**' nde, model öğesinin kısayol menüsünü açın. Bağlantılı iş öğelerinin listesini görüntülemek için **Iş öğelerini görüntüle** ' yi seçin.

    > [!NOTE]
    > Yalnızca bağlı olan sunucudaki iş öğeleri görünür. Herhangi bir iş öğesi görmüyorsanız, **Takım Gezgini**doğru sunucuya bağlı olduğunuzdan emin olun.

## <a name="ViewLinkedModels"></a>İş öğesine bağlı model öğelerini görüntüle
 Visual Studio Team Services ve Team Foundation Server 2012 veya sonraki bir sürümde bir iş öğesiyle bağlantılı olan modelleme diyagramlarını ve öğelerini görüntüleyebilirsiniz. Örneğin, bir iş öğesi uygulanacak yeni sınıfların tasarımını gösteren sınıf modellerine bağlı olabilir.

1. **Takım Gezgini**, model öğelerinin iş öğesiyle bağlantılı olduğu takım projesine bağlı olduğunuzdan emin olun.

    > [!NOTE]
    > Bağlantılı model öğelerini görüntülemek için yalnızca Takım Gezgini'ni kullanabilirsiniz; Team Web Access'i kullanamazsınız. Çalışma alanınızın modelleme diyagramlarını veya öğeleri içeren modelleme projesiyle eşleştiğinden emin olun. Çalışma alanınız yoksa, oluşturmanız gerekir. Bkz. [sorun giderme](#Troubleshooting) ve çalışma [alanları oluşturma ve bunlarla çalışma](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).

2. İş öğesini açın, **Bağlantılar**' ı seçin. **Model bağlantısı**altında, bağlantılı model öğesinin kısayol menüsünü açın. **Bağlı öğeyi aç**' ı seçin.

     ![Bağlı model öğesini bir iş öğesinden aç](../modeling/media/workitem-openlinkedmodelelement.png "WorkItem_OpenLinkedModelElement")

## <a name="RemoveLinks"></a>Model öğeleri ve iş öğeleri arasındaki bağlantıları sil
 Model öğesinden başlayarak bağlantılı bir iş öğesini kaldırın. Bu, model öğesinin ters bağlantısını iş öğesinden kaldırır. Aksi takdirde, iş öğesiyle başlarsanız, model öğesinden iş öğesine giden ters bağlantı silinmez.

1. Modelleme diyagramında veya **UML Model Gezgini**' nde, model öğesinin kısayol menüsünü açın.

2. **Iş öğelerini kaldır**' ı seçin.

     \- veya-

    1. **Özellikler**' i ve ardından bağlantılı iş öğesi sayısının göründüğü **iş öğelerini** seçin.

    2. **Iş öğeleri** özelliğinde, üç nokta düğmesini ( **[...]** ) seçin.

        > [!NOTE]
        > Yalnızca geçerli sunucudaki iş öğeleri görünür. Liste boşsa, ancak iş öğelerinin sayısı sıfır değilse, **Takım Gezgini**doğru sunucuya bağlandığınızdan emin olun.

3. **Iş öğelerinin bağlantılarını kaldır**' ın altında, bağlantısını kaldırmak istediğiniz seçili öğeleri temizleyin. **Tamam ' ı**seçin.

## <a name="Troubleshooting"></a>Sorunu

|**Konuda**|**Olası neden**|**Çözünürlüğüne**|
|---------------|------------------------|--------------------|
|Bağlamak istediğiniz model öğesi bulunamıyor.|Öğesi, [!INCLUDE[esprscc](../includes/esprscc-md.md)] bir modelleme projesindeki diyagramda olabilir. Diyagramla eşleşen bir çalışma alanınız olmayabilir.|Çalışma alanınızı modelleme projesiyle ve diyagramla eşleştirin. Çalışma alanınız yoksa, oluşturmanız gerekir.<br /><br /> Bu sorun için görünen hata iletisi, çalışma alanınızı eşleştirmek için kullanabileceğiniz yolu içerir.<br /><br /> Bkz. [çalışma alanları oluşturma ve bunlarla çalışma](https://msdn.microsoft.com/library/1d7f6ed8-ec7c-48f8-86da-9aea55a90d5a).|
|Bağlantılı model öğesi bulunamıyor.|Bağlantılı öğe taşınmış, yeniden adlandırılmış veya silinmiş bir diyagram üzerinde olabilir.|1. iş öğesinde model öğesinin bağlantısını silin.<br />2. iş öğesinden model öğesine yeni bir bağlantı oluşturun.|
|İş öğesinde beklediğiniz bağlantılı model öğeleri yoktur.|Bir iş öğesi, yalnızca bağlantılı iş öğesinden oluşturulmuşsa bağlantılı katmanı öğesini gösterir. Takımınız [!INCLUDE[esprscc](../includes/esprscc-md.md)] kullanmıyorsa, diyagramların yerel yolu bağlantıları oluşturmak için kullanılır. Modelleme projesi ve diyagramları [!INCLUDE[esprscc](../includes/esprscc-md.md)] ise, projeye erişebilen tüm ekip üyeleri iş öğelerinde bağlantılı öğeleri görüntüleyebilir.|İş öğesini yenilemeyi deneyin.|
|Bir iş öğesinden model öğesine giden bağlantının silinmesi, model öğesinden iş öğesine giden bağlantıyı silmez.||Model öğesinden başlayarak iş öğesine giden bağlantıyı silin.|

## <a name="see-also"></a>Ayrıca Bkz.
 [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md) [uygulamanız için modeller oluşturma](../modeling/create-models-for-your-app.md)
