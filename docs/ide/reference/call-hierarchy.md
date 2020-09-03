---
title: Bir yönteme çağrı bulma
ms.date: 05/18/2018
ms.topic: reference
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcedc6a49c0df84b4482f8030524d59d4336bcc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595806"
---
# <a name="view-call-hierarchy"></a>Çağrı hiyerarşisini görüntüle

Kodunuzun Çağrı hiyerarşisini görüntüleyerek, seçilen bir yöntem, özellik veya oluşturucunun tüm çağrılarına ve bazı çağrılarına gidebilirsiniz. Bu, kodun akışını daha iyi anlamanıza ve koddaki değişikliklerin etkilerini değerlendirmenize olanak sağlar. Yöntem çağrılarının karmaşık zincirlerini ve koda ek giriş noktalarını görüntülemek için çeşitli kod düzeylerini inceleyebilirsiniz. Bu, tüm olası yürütme yollarını incelemenize olanak sağlar.

Visual Studio 'da, bir çağrı hiyerarşisini tasarım zamanında görüntüleyebilirsiniz. Bu, bir kesme noktası ayarlamanız ve çalışma zamanı çağrı yığınını görüntülemek için hata ayıklayıcıyı başlatmanız gerekmediği anlamına gelir.

## <a name="use-the-call-hierarchy-window"></a>Çağrı hiyerarşisi penceresini kullanın

**Çağrı hiyerarşisi** penceresini görüntülemek için, bir yöntem, özellik veya Oluşturucu çağrısının adı üzerinde kod Düzenleyicisi ' ne sağ tıklayın ve ardından **Çağrı hiyerarşisini görüntüle**' yi seçin.

Üye adı, **çağrı hiyerarşisi** penceresindeki bir ağaç görünümü bölmesinde görünür. Üye düğümünü genişletirseniz, *üye adına* **çağrılar** ve C++ için *üye adından* **çağrılar** , alt düğümler görüntülenir.

C++ kodu için, bir üyeye hem hem de bir üyenin aramalarını görebilirsiniz:

![Visual Studio 'da C++ kodu için çağrı hiyerarşisi](media/call-hierarchy-cpp.png)

C# ve Visual Basic kodu için, bir üyeye yapılan çağrıları görebilir, ancak şuradan çağrı yapabilirsiniz:

![Visual Studio 'da C# kodu için çağrı hiyerarşisi](media/call-hierarchy-csharp.png)

- Düğüme yapılan **çağrıları** genişletirseniz, seçilen üyeyi çağıran tüm Üyeler görüntülenir.

- C++ için, düğümdeki **çağrıları** genişlettikten sonra seçili üye tarafından çağrılan tüm Üyeler görüntülenir.

Ardından, **çağrılarını**görmek için her bir çağıran üyeyi genişletebilir ve C++ Için düğümlerden **çağrılar** yapabilirsiniz. Bu, aşağıdaki görüntüde gösterildiği gibi çağıranların yığınına gitmenizi sağlar:

![Birden çok düzey genişletilen hiyerarşi çağrısı penceresi](media/call-hierarchy-csharp-expanded.png)

Sanal veya soyut olarak tanımlanan üyeler için bir **geçersiz kılma yöntemi adı** düğümü görüntülenir. Arabirim üyeleri için bir **Implements Yöntem adı** düğümü görüntülenir. Bu **Genişletilebilir düğümler** **, ve düğümlerin çağrılarıyla** aynı düzeyde görüntülenir.

Araç çubuğundaki **arama kapsamı** kutusu **çözümünüz**, **geçerli proje**ve **geçerli belge**için seçenekler içerir.

**Çağrı hiyerarşisi** ağacı görünüm bölmesinde bir alt üye seçtiğinizde:

- **Çağrı hiyerarşisi** ayrıntıları bölmesi, alt üyenin üst Üyeden çağrıldığı tüm kod satırlarını görüntüler.

- **Kod tanımı** penceresi açıksa, seçili üye için kodu görüntüler (yalnızca C++). Bu pencere hakkında daha fazla bilgi için bkz. [kod yapısını görüntüleme](../../ide/viewing-the-structure-of-code.md).

> [!NOTE]
> **Çağrı hiyerarşisi** özelliği, bir yöntemin olay işleyicisi olarak eklendiği veya bir temsilciye atandığı yerleri içeren, metot grubu başvurularını bulmaz. Bir yönteme yapılan tüm başvuruları bulmak için, **tüm başvuruları bul** komutunu kullanabilirsiniz.

## <a name="shortcut-menu-items"></a>Kısayol menü öğeleri

Aşağıdaki tabloda, ağaç görünümü bölmesinde bir düğüme sağ tıkladığınızda kullanılabilecek çeşitli kısayol menü seçenekleri açıklanmaktadır.

|Bağlam menüsü öğesi|Description|
| - |-----------------|
|**Yeni kök olarak ekle**|Seçili düğümü ağaç görünümü bölmesine yeni bir kök düğüm olarak ekler. Bu, ilgilenmeniz belirli bir alt ağaçta odaklanmanızı sağlar.|
|**Kökü Kaldır**|Seçili kök düğümü ağaç görünümü bölmesinden kaldırır. Bu seçenek yalnızca bir kök düğümden kullanılabilir.<br /><br /> Seçili kök düğümü kaldırmak için **kök kaldır** araç çubuğu düğmesini de kullanabilirsiniz.|
|**Tanıma Git**|Seçili düğümdeki Tanıma Git komutunu çalıştırır. Bu, bir üye çağrısının veya değişken tanımının orijinal tanımına gider.<br /><br /> Tanıma Git komutunu çalıştırmak için Seçili düğüme çift tıklayabilir veya seçili düğümdeki F12 tuşuna basabilirsiniz.|
|**Tüm Başvuruları Bul**|Seçili düğümdeki tüm başvuruları bul komutunu çalıştırır. Bu, projenizdeki bir sınıfa veya üyeye başvuran tüm kod satırlarını bulur.<br /><br /> Seçili düğümdeki tüm başvuruları bul komutunu çalıştırmak için SHIFT + F12 tuşlarını da kullanabilirsiniz.|
|**Kopyala**|Seçili düğümün içeriğini kopyalar (alt düğümleri değil).|
|**Yenile**|Seçili düğümü, yeniden genişleterek geçerli bilgileri görüntüleyecek şekilde daraltır.|
