---
title: Yönteme yapılan çağrıları bulma
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595806"
---
# <a name="view-call-hierarchy"></a>Arama hiyerarşisi görüntüle

Kodunuz için çağrı hiyerarşisini görüntüleyerek, seçili bir yönteme, özellike veya oluşturucuya yapılan tüm aramalarda ve bazen de bu çağrılardan gidebilirsiniz. Bu, kodun nasıl aktığını daha iyi anlamanızı ve koddaki değişikliklerin etkilerini değerlendirmenizi sağlar. Yöntem çağrılarının karmaşık zincirlerini ve koda ek giriş noktalarını görüntülemek için çeşitli kod düzeylerini inceleyebilirsiniz. Bu, olası tüm yürütme yollarını keşfetmenizi sağlar.

Visual Studio'da, tasarım zamanında bir çağrı hiyerarşisi görüntüleyebilirsiniz. Bu, bir kesme noktası ayarlamak ve çalışma zamanı arama yığınını görüntülemek için hata ayıklama başlatmak zorunda değilsiniz anlamına gelir.

## <a name="use-the-call-hierarchy-window"></a>Çağrı Hiyerarşisi penceresini kullanma

**Çağrı Hiyerarşisi** penceresini görüntülemek için, kod düzenleyicisi'ni bir yöntemin, özelliğin veya oluşturucu çağrısının adına sağ tıklatın ve ardından **Çağrı Hiyerarşisini Görüntüle'yi**seçin.

Üye **adı, Çağrı Hiyerarşisi** penceresindeki bir ağaç görünümü bölmesinde görünür. Üye düğümündeki leri genişletirseniz, *Üye adına* **Çağrılar** ve C++, *Üye Adından* **Gelen Aramalar** , subnodes görünür.

C++ kodu için, hem üyeye hem de üyeden gelen aramaları görebilirsiniz:

![Visual Studio'da C++ kodu için Çağrı Hiyerarşisi](media/call-hierarchy-cpp.png)

C# ve Visual Basic kodu için, bir üyeye yapılan aramaları görebilir, ancak şu andan gelen çağrıları göremezsiniz:

![Visual Studio'da C# kodu için Çağrı Hiyerarşisi](media/call-hierarchy-csharp.png)

- **Çağrıları Düğüme** genişletirseniz, seçili üyeyi arayan tüm üyeler görüntülenir.

- C++'da, **düğümden Gelen Çağrıları** genişletirseniz, seçili üye tarafından çağrılan tüm üyeler görüntülenir.

Daha sonra her çağrı **üyesini, Çağrılarını**ve C++'ı için **Düğümlerden Gelen Çağrıları** görmek için genişletebilirsiniz. Bu, aşağıdaki resimde gösterildiği gibi, arayanlar yığınına gezinmenizi sağlar:

![Birden çok düzeyi genişletilmiş Çağrı Hiyerarşisi penceresi](media/call-hierarchy-csharp-expanded.png)

Sanal veya soyut olarak tanımlanan üyeler için geçersiz **kılma yöntemi ad** düğümü görüntülenir. Arabirim üyeleri için bir **Uygulama yöntemi ad** düğümü görüntülenir. Bu genişletilebilir düğümler, Çağrılar ve **Düğümlerden Gelen** **Aramalar** ile aynı düzeyde görünür.

Araç çubuğundaki **Arama Kapsamı** **kutusu, Çözüm,** **Geçerli Projem**ve **Geçerli Belgem**için seçenekler içerir.

**Çağrı Hiyerarşisi** ağaç görünümü bölmesinde bir alt üye seçtiğinizde:

- **Çağrı Hiyerarşisi** ayrıntıları bölmesi, alt üyenin üst üyeden çağrıldığı tüm kod satırlarını görüntüler.

- **Kod Tanımı** penceresi, açıksa, seçili üyenin kodunu görüntüler (yalnızca C++). Bu pencere hakkında daha fazla bilgi için [bkz.](../../ide/viewing-the-structure-of-code.md)

> [!NOTE]
> **Çağrı Hiyerarşisi** özelliği, yöntemin olay işleyicisi olarak eklendiği veya bir temsilciye atandığı yerleri içeren yöntem grubu başvurularını bulamaz. Bir yönteme yapılan tüm başvuruları bulmak için **Tüm Başvuruları Bul** komutunu kullanabilirsiniz.

## <a name="shortcut-menu-items"></a>Kısayol menü öğeleri

Aşağıdaki tabloda, ağaç görünümü bölmesinde bir düğümü sağ tıklattığınızda kullanılabilen birkaç kısayol menüsü seçeneği açıklanmaktadır.

|Bağlam Menü Öğesi|Açıklama|
| - |-----------------|
|**Yeni Kök Olarak Ekle**|Seçili düğümü yeni bir kök düğümü olarak ağaç görünümü bölmesine ekler. Bu, dikkatinizi belirli bir alt ağaca odaklamanızı sağlar.|
|**Kök kaldırma**|Seçili kök düğümünü ağaç görünüm bölmesinden kaldırır. Bu seçenek yalnızca bir kök düğümünden kullanılabilir.<br /><br /> Seçili kök düğümünü kaldırmak için Kök çubuğunu **kaldır** düğmesini de kullanabilirsiniz.|
|**Tanıma Git**|Seçili düğümde Tanıma Git komutunu çalıştırın. Bu, üye çağrısı veya değişken tanımı için özgün tanıma yönlendirin.<br /><br /> Tanıma Git komutunu çalıştırmak için, seçili düğüme çift tıklayabilir veya seçili düğümde F12 tuşuna basabilirsiniz.|
|**Tüm Başvuruları Bul**|Seçili düğümdeki Tüm Başvuruları Bul komutunu çalıştırın. Bu, projenizde bir sınıfa veya üyeye başvuru yapan tüm kod satırlarını bulur.<br /><br /> Shift+F12'yi seçili düğümdeki Tüm Başvuruları Bul komutunu çalıştırmak için de kullanabilirsiniz.|
|**Kopyala**|Seçili düğümün içeriğini kopyalar (ancak alt düğümlerini değil).|
|**Yenile**|Seçili düğümü daraltarak yeniden genişleten geçerli bilgileri görüntüler.|
