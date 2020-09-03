---
title: Çağrı hiyerarşisi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
ms.assetid: c55bda01-d7de-4823-8f9a-1bcc37dbb74a
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 823c61e7625850c680b52cd4ad9386ef0838d340
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660928"
---
# <a name="call-hierarchy"></a>Çağrı Hiyerarşisi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Çağırma hiyerarşisi, seçili bir yöntem, özellik veya oluşturucuya tüm çağrıları görüntüleyerek kodunuzda gezinmenize olanak sağlar. Bu, kodun akışını daha iyi anlamanıza ve koddaki değişikliklerin etkilerini nasıl değerlendirmenize olanak sağlar. Yöntem çağrılarının karmaşık zincirlerini ve koda ek giriş noktalarını görüntülemek için, olası tüm yürütme yollarını incelemenize olanak sağlayan çeşitli kod düzeylerini inceleyebilirsiniz.

 Çağrı hiyerarşisi, hata ayıklayıcı tarafından görüntülenen çağrı yığınının aksine tasarım zamanında kullanılabilir.

## <a name="using-call-hierarchy"></a>Çağrı hiyerarşisini kullanma
 **Çağrı hiyerarşisi** penceresini görüntülemek için bir yöntem, özellik veya Oluşturucu çağrısının adına sağ tıklayın ve ardından **Çağrı hiyerarşisini görüntüle**' ye tıklayın.

 Üye adı, **çağrı hiyerarşisi** penceresindeki bir ağaç görünümü bölmesinde görünür. Üye düğümünü **genişletirseniz üye adı**_ve alt_ **düğümlere yapılan çağrılar**_member name_ görüntülenir. Aşağıdaki çizim, bu düğümleri **çağrı hiyerarşisi** penceresinde gösterir.

 ![Tek düğümlü Açık hiyerarşi çağırma](../../ide/reference/media/onenode.png "OneNode") Çağrı hiyerarşisi penceresi

- Düğüme yapılan **çağrıları** genişletirseniz, seçilen üyeyi çağıran tüm Üyeler görüntülenir.

- **Çağrıları** düğümünden genişletirseniz, seçilen üye tarafından çağrılan tüm Üyeler görüntülenir.

  Daha sonra bu alt düğüm üyelerinden her birini, düğümlere yapılan **çağrılara** ve **çağrılar halinde** genişletebilirsiniz. Bu, aşağıdaki çizimde gösterildiği gibi çağıranların yığınına gitmenizi sağlar.

  ![Çağrı hiyerarşisi birden çok düğüm açık](../../ide/media/multiplenodes.png "MultipleNodes") Çağrı hiyerarşisi penceresi

  Sanal veya soyut olarak tanımlanan üyeler için bir **geçersiz kılma yöntemi adı** düğümü görüntülenir. Arabirim üyeleri için bir **Implements Yöntem adı** düğümü görüntülenir. Bu **Genişletilebilir düğümler** **, ve düğümlerin çağrılarıyla** aynı düzeyde görüntülenir.

  Araç çubuğundaki **arama kapsamı** kutusu **çözümünüz**, **geçerli proje**ve **geçerli belge**için seçenekler içerir.

  **Çağrı hiyerarşisi** ağacı görünüm bölmesinde bir alt üye seçtiğinizde:

- **Çağrı hiyerarşisi** ayrıntıları bölmesi, alt üyenin üst Üyeden çağrıldığı tüm kod satırlarını görüntüler.

- **Kod tanımı penceresi**açıksa, seçilen üyenin kodunu görüntüler. Bu pencere C# ve C++ ' da kullanılabilir. Bu pencere hakkında daha fazla bilgi için bkz. [kod yapısını görüntüleme](../../ide/viewing-the-structure-of-code.md).

> [!NOTE]
> Çağrı hiyerarşisi, bir yöntemin bir olay işleyicisi olarak eklendiği veya bir temsilciye atandığı yerleri içeren, metot grubu başvurularını bulamaz. Bir yönteme yapılan tüm başvuruları bulmak için, **tüm başvuruları bul** komutunu kullanabilirsiniz.

## <a name="shortcut-menu-items"></a>Kısayol menü öğeleri
 Aşağıdaki tabloda, ağaç görünümü bölmesinde bir düğüme sağ tıkladığınızda kullanılabilecek çeşitli kısayol menü seçenekleri açıklanmaktadır.

|Bağlam menüsü öğesi|Açıklama|
|-----------------------|-----------------|
|**Yeni kök olarak ekle**|Seçili düğümü ağaç görünümü bölmesine yeni bir kök düğüm olarak ekler. Bu, ilgilenmeniz belirli bir alt ağaçta odaklanmanızı sağlar.|
|**Kökü Kaldır**|Seçili kök düğümü ağaç görünümü bölmesinden kaldırır. Bu seçenek yalnızca bir kök düğümden kullanılabilir.<br /><br /> Seçili kök düğümü kaldırmak için **kök kaldır** araç çubuğu düğmesini de kullanabilirsiniz.|
|**Tanıma Git**|Seçili düğümdeki Tanıma Git komutunu çalıştırır. Bu, bir üye çağrısının veya değişken tanımının orijinal tanımına gider.<br /><br /> Tanıma Git komutunu çalıştırmak için Seçili düğüme çift tıklayabilir veya seçili düğümdeki F12 tuşuna basabilirsiniz.|
|**Tüm Başvuruları Bul**|Seçili düğümdeki tüm başvuruları bul komutunu çalıştırır. Bu, projenizdeki bir sınıfa veya üyeye başvuran tüm kod satırlarını bulur.<br /><br /> Seçili düğümdeki tüm başvuruları bul komutunu çalıştırmak için SHIFT + F12 tuşlarını da kullanabilirsiniz.|
|**Kopyala**|Seçili düğümün içeriğini kopyalar (alt düğümleri değil).|
|**Yenile**|Seçili düğümü, yeniden genişleterek geçerli bilgileri görüntüleyecek şekilde daraltır.|
