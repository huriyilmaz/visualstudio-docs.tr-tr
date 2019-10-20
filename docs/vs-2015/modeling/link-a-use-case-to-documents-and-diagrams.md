---
title: Kullanım örneğini belgelere ve diyagramlara bağlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties.artifactlink
- vs.teamarch.usecasediagram.artifact
helpviewer_keywords:
- use case diagrams
ms.assetid: 4c9ed205-9197-4ed5-b39d-ddfa24a0a421
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c713759a8ea75eed3048469327f962668efa4f70
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657648"
---
# <a name="link-a-use-case-to-documents-and-diagrams"></a>Kullanım örneğini belgelere ve diyagramlara bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanım örneği diyagramında kullanım örneğini başka bir diyagrama veya belgeye bağlayabilirsiniz. Örneğin, kullanım örneğini aşağıdaki diyagramlara ve belgelere bağlayabilirsiniz:

- Kullanım örneği hedeflerinin kullanıcılar ve sistem ile ana bileşenleri arasındaki etkileşimler tarafından nasıl yapıldığını gösteren bir sıralı diyagram.

- Kullanım örneğini gerçekleştirirken kullanıcıların ve sistemin ya da onun ana bileşenlerinin ayrıntılı eylemlerini gösteren bir etkinlik diyagramı.

- Kullanım örneğini ayrıntılı olarak açıklayan bir OneNote sayfası veya paragrafı.

- Kullanım örneğini ayrıntılı olarak açıklayan bir Word belgesi veya PowerPoint sunusu. Bu tür belgeleri çözümde veya SharePoint sitesi gibi ekibiniz tarafından erişilebilen bir konumda tutabilirsiniz.

  Kullanım örneğini bir belgeye bağlamak için kullanım durumu diyagramında bir yapıt oluşturur ve kullanım örneğini yapıtı bağlayın. Yapının özelliklerinde, diğer diyagramın veya belgenin dosya yolunu ayarlarsınız. Yapıtı çift tıklattığınızda, diğer diyagram veya belge açılır.

  İstediğiniz her kullanım örneğine çok sayıda yapıt bağlayabilirsiniz. Ayrıca, yapıları kullanım örneği diyagramında diğer öğe türlerine bağlayabilirsiniz.

### <a name="to-open-a-document-associated-with-an-artifact"></a>Yapıtla ilişkili bir belgeyi açmak için

- Kullanım durumu diyagramında, yapıt şekline çift tıklayın.

     İlişkili belge açılır.

### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Bir kullanım durumunu aynı çözümdeki bir diyagrama veya dosyaya bağlamak için

1. Kullanım durumunun bir senaryosunu göstermek için sıralı diyagram veya etkinlik diyagramı gibi bir diyagram çizin.

2. Kullanım durumu diyagramına geri dönün.

3. Çözüm Gezgini diyagramı veya dosyayı kullanım durumu diyagramının boş bir bölümüne sürükleyin.

4. Bir **bağımlılığı**kullanarak yapıtın kullanım örneğine bağlanın.

### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Word belgesi veya PowerPoint sunusu gibi bir çözüm dosyasına bağlantı sağlamak için

1. Belgeyi çözüme ekleyin.

    1. Word belgesini çözümle aynı Windows klasörüne taşıyın.

    2. Çözüm Gezgini, çözüme sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **var olan öğe**' ye tıklayın.

    3. Word belgesine gidin ve **Ekle**' ye tıklayın.

         Word belgesi, Çözüm Gezgini bir çözüm klasöründe görüntülenir.

2. Word belgesini Çözüm Gezgini ' den kullanım durumu diyagramının boş bir bölümüne sürükleyin.

     Yeni bir yapıt görüntülenir.

3. Bir **bağımlılığı**kullanarak yapıtın kullanım örneğine bağlanın.

### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Paylaşılan bir belgeye, OneNote öğesine veya Web sayfasına bağlamak için

1. Paylaşılan öğenin URL 'sini alın. Bu, örneğin, ' \\ \\ ' veya bir Web sayfası veya SharePoint URL 'SI ' http://' ile başlayan bir ağ dosyası yolu ya da ' OneNote: ' başlangıcında bir OneNote bölümü, sayfası veya paragrafı bağlantısı olabilir.

2. Araç kutusunda **yapıt** ' ye ve ardından kullanım durumu diyagramında ' a tıklayın.

3. Seçilen yeni yapıt ile URL 'YI yazın veya **köprü** özelliğine yapıştırın.

    > [!NOTE]
    > Bir dosya yolu sağlamak istiyorsanız, ortak bir çalışma alanında (' \\ \\ ' ile başlayarak) veya Visual Studio çözümünüzün içindeki bir dosyayı seçmek en iyisidir. Bu, dosya yolunun başka bir takım üyesinin bilgisayarında geçerli kalmasını veya çözümün taşınabilmesini sağlar. Çözümünüze Word belgesi gibi bir belge eklemek için Çözüm Gezgini ' de çözüme sağ tıklayın, **Ekle** ' nin üzerine gelin ve **var olan öğe**' ye tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [UML Kullanım örneği diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md) [UML Kullanım örneği DIYAGRAMLARı: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md) [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md) [uygulamanız için modeller oluşturma](../modeling/create-models-for-your-app.md)
