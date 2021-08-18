---
title: Yöntem çağrılarını bulma
description: Çağrı Hiyerarşisi penceresini kullanarak bazı durumlarda seçilen yönteme, özele veya oluşturucuya yapılan tüm çağrılara nasıl gidileceklerini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/18/2018
ms.topic: reference
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 97f6e4a351267c5cd26ad283ecdf6cc49cf2e8620707805dd0234c708ff9b698
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121430901"
---
# <a name="view-call-hierarchy"></a>Çağrı hiyerarşisini görüntüleme

Kodunuzun çağrı hiyerarşisini görüntüerek, bazen seçilen yöntem, özellik veya oluşturucuya yapılan tüm çağrılarda gezinebilirsiniz. Bu sayede kod akışlarını daha iyi anabilir ve kod üzerindeki değişikliklerin etkilerini değerlendirebilirsiniz. Karmaşık yöntem çağrı zincirlerini ve koda ek giriş noktalarını görüntülemek için çeşitli kod düzeylerini inceebilirsiniz. Bu sayede tüm olası yürütme yollarını keşfedersiniz.

Bu Visual Studio tasarım zamanında bir çağrı hiyerarşisini görüntüebilirsiniz. Bu, çalışma zamanı çağrı yığınını görüntülemek için bir kesme noktası ayarlamak ve hata ayıklayıcıyı başlatmak zorunda olmadığınız anlamına gelir.

## <a name="use-the-call-hierarchy-window"></a>Çağrı Hiyerarşisi penceresini kullanma

Çağrı **Hiyerarşisi penceresini görüntülemek** için bir yöntem, özellik veya oluşturucu çağrısının adına kod düzenleyicisine sağ tıklayın ve Çağrı Hiyerarşisini **Görüntüle'yi seçin.**

Üye adı, Çağrı Hiyerarşisi penceresindeki bir ağaç **görünümü bölmesinde** görünür. Üye düğümünü genişleterseniz, **Üye** adına *çağrılar* ve C++ için Üye **adına** *çağrılar*, alt düğümleri görünür.

C++ kodu için bir üyeye ve üyeden gelen çağrıların ikisini de görebilir:

![Visual Studio'de C++ kodu için Hiyerarşi çağırma](media/call-hierarchy-cpp.png)

C# ve Visual Basic için, üyeye yapılan çağrıları görebilir, ancak şu çağrılardan çağırabilirsiniz:

![Visual Studio'de C# kodu için Hiyerarşiyi çağırma](media/call-hierarchy-csharp.png)

- Çağrılar **düğümünü genişletseniz,** seçilen üyeyi çağıran tüm üyeler görüntülenir.

- C++ için, Seçilen üye **tarafından çağrılyan** tüm üyeler görüntülenir.

Daha sonra her bir çağrı üyesini genişletecek ve C++ için düğümlerden Yapılan **Çağrılar'ı görebilirsiniz.** Bu, aşağıdaki görüntüde gösterildiği gibi çağrıyı yapanlar yığınına gezinmenizi sağlar:

![Birden çok düzey genişletilmiş Çağrı Hiyerarşisi penceresi](media/call-hierarchy-csharp-expanded.png)

Sanal veya soyut olarak tanımlanan üyeler için bir **Overrides yöntem adı** düğümü görünür. Arabirim üyeleri için **Implements yöntem adı düğümü** görünür. Bu genişletilebilir düğümler, Çağrılar ve **Düğümlerden Çağrılar** **ile aynı düzeyde** görünür.

Araç **çubuğundaki** Arama Kapsamı kutusu Çözümüm, Geçerli Project **ve** Geçerli Belge **seçenekleri içerir.**

Hiyerarşiyi Çağır ağaç görünümü bölmesinde **bir alt üyeyi** seçerek:

- Çağrı **Hiyerarşisi** ayrıntıları bölmesi, bu alt üyenin üst üyeden çağrıldı olduğu tüm kod satırlarını görüntüler.

- Kod **Tanımı penceresi** açıksa, seçilen üyenin kodunu görüntüler (yalnızca C++). Bu pencere hakkında daha fazla bilgi için [bkz. Kodun yapısını görüntüleme.](../../ide/viewing-the-structure-of-code.md)

> [!NOTE]
> Çağrı **Hiyerarşisi** özelliği, bir yöntemin olay işleyicisi olarak ekli olduğu veya bir temsilciye atandığı yerleri içeren yöntem grubu başvurularını bulmaz. Bir yönteme yapılan tüm başvuruları bulmak için Tüm Başvuruları Bul **komutunu kullanabilirsiniz.**

## <a name="shortcut-menu-items"></a>Kısayol menü öğeleri

Aşağıdaki tabloda, ağaç görünümü bölmesinde bir düğüme sağ tıklarken kullanılabilen birkaç kısayol menüsü seçeneği açık almaktadır.

|Bağlam Menüsü Öğesi|Açıklama|
| - |-----------------|
|**Yeni Kök Olarak Ekle**|Seçilen düğümü ağaç görünümü bölmesine yeni bir kök düğüm olarak ekler. Bu, dikkatlerinizi belirli bir alt ağacına odaklanmanızı sağlar.|
|**Kök Kaldır**|Seçili kök düğümü ağaç görünümü bölmesinden kaldırır. Bu seçenek yalnızca bir kök düğümden kullanılabilir.<br /><br /> Seçili kök düğümü kaldırmak **için Kök araç** çubuğunu kaldır düğmesini de kullanabilirsiniz.|
|**Tanıma Git**|Seçili düğümde Tanıma Git komutunu çalıştırır. Bu, bir üye çağrısının veya değişken tanımının özgün tanımına gidin.<br /><br /> Tanıma Git komutunu çalıştırmak için seçilen düğüme çift tıklar veya seçili düğümde F12 tuşuna basabilirsiniz.|
|**Tüm Başvuruları Bul**|Seçili düğümde Tüm Başvuruları Bul komutunu çalıştırır. Bu, projenizin bir sınıf veya üyeye başvuran tüm kod satırlarını bulur.<br /><br /> Seçilen düğümde Tüm Başvuruları Bul komutunu çalıştırmak için SHIFT+F12 de kullanabilirsiniz.|
|**Kopyala**|Seçilen düğümün içeriğini kopyalar (ancak alt düğümlerini kopyalar).|
|**Yenile**|Seçilen düğümü daraltarak yeniden genişleterek geçerli bilgileri görüntülemesini sağlar.|
