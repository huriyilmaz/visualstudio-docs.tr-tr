---
title: Domain-Specific Dil Araçları kullanıcı arabirimine genel bakış
description: Etki alanına özgü dil araçları çözümünün kullanıcı arabirimine genel bir bakış sağlar Visual Studio.
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 4fe826b373ba2ee468bfe511392eb5564234dc68
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390964"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Etki Alanına Özgü Dil Araçları Kullanıcı Arabirimine Genel Bakış
Visual Studio'de Domain-Specific Dil Araçları (DSL Araçları) çözümünü ilk kez Visual Studio kullanıcı arabirimi aşağıdaki resme benzer.

 ![dsl tasarımcısı](../modeling/media/dsl_designer.png)

 Aşağıdaki tabloda kullanıcı arabirimi bölümlerinin nasıl kullanıldıkları açıklanmış.

|**Öğe**|**Tanım**|
|-|-|
|Diyagram|Diyagramda etki alanı modeli görüntülenir.<br /><br /> Diyagramın iki tarafı vardır. Bir taraf, modelleriniz içinde öğelerin türlerini tanımlar. Diğer taraftan modellerinizi ekranda nasıl görüntüleyebilirsiniz?|
|Araç Kutusu|Diyagrama etki alanı sınıfları ve şekil türleri eklemek için araçları araç kutusundan sürükleyin. İlişki, bağlayıcı ve şekil eşlemeleri eklemek için, aracı tıklatın, ardından diyagramda kaynak düğüme ve ardından hedef düğüme tıklayın.|
|DSL Gezgini|**DSL Gezgini,** DSL tanımı etkin pencere olduğunda görüntülenir. DSL'i ağaç olarak gösterir. DSL Gezgini, diyagramda görüntülenmeen modelin özelliklerini düzenlemenizi sağlar. Örneğin, DSL Gezgini'ni kullanarak araç kutusu öğeleri ekleyebilir ve doğrulama işlemini **kullanabilirsiniz.**|
|DSL Ayrıntıları penceresi|**DSL Ayrıntıları penceresi,** etki alanı modelinin öğelerin nasıl görüntülendiğinden ve öğelerin nasıl kopyalanır ve silindikten sonra nasıl silineceklerini denetlemeye olanak sağlayan özelliklerini gösterir.<br /><br /> - Varsayılan olarak, **Hata Listesi ve** Çıkış pencerelerinin yanında DSL **Ayrıntıları** **penceresi** görünür.|

## <a name="the-domain-model-diagram"></a>Etki Alanı Modeli Diyagramı
 Etki alanı modeli diyagramı iki bölüme ayrılır. Diyagramın bir tarafında modelde öğeler ve ilişkiler yer almaktadır. Diğer taraf, modelin nasıl görüntülendiğinden ve model diyagramının öğelerini ve özelliklerini görüntülemek için kullanılan şekilleri içerir. Aşağıdaki resim diyagramın öğelerini gösterir.

 ![kullana sahip dsl tasarımcısı](../modeling/media/dsl_desinger.png)

 Aşağıdaki tabloda etki alanı modeli diyagramının bazı öğeleri açık açıklamalır.

|**Süre**|**Tanım**|
|-|-|
|Etki Alanı Sınıfı|Etki alanı sınıfları, modelleriniz içinde yer alan öğe türleridir.<br /><br /> Birden fazla ilişkinin hedefi ise, bir etki alanı sınıfı diyagramda birden çok kez görünebilir.<br /><br /> Bir etki alanı sınıfı eklemek için, etki alanı sınıfı aracını **Araç Kutusundan** diyagramın **Sınıflar ve İlişkiler** tarafına sürükleyin.|
|Etki Alanı İlişkisi|Etki alanı ilişkileri, modelleriniz arasındaki bağlantı türleridir.<br /><br /> Ekleme *ilişkisi, hedef* öğenin sahip olduğunu veya kaynak öğeye ait olduğunu gösterir ve düz çizgi olarak görünür. Modeldeki her öğe bir ekleme ilişkisinin hedefi olmalı, böylece model bir ağaç oluşturur. Başvuru *ilişkisi,* model öğeleri arasındaki genel bir bağlantıyı gösterir ve kesikli çizgi olarak görünür. Herhangi bir öğe, herhangi bir sayıda başvuru bağlantısına sahip olabilir.<br /><br /> Araç Kutusunda aracına tıklayarak, kaynak etki **alanı** sınıfına ve ardından hedef sınıfa tıklayarak bir ilişki oluşturun.|
|Şekiller ve Bağlayıcılar|Şekiller, model öğelerinin DSL diyagramında nasıl görüntülenebilir olduğunu belirtir. Bağlayıcılar, ilişkileri görüntülemek için kullanılan DSL diyagramında çizgileri belirtir.<br /><br /> Şekil veya bağlayıcı oluşturmak için, aracı diyagramın **Diyagram Öğeleri** tarafına sürükleyin.|
|Şekil Haritaları|Şekil haritası, etki alanı modeli diyagramında çizgi olarak görünür ve bir şekli, görüntülenilen etki alanı sınıfına veya görüntülenilen etki alanı ilişkisine bir bağlayıcıya bağlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Etki Alanına Özgü Dil Araçlarına Genel Bakış](../modeling/overview-of-domain-specific-language-tools.md)
- [Alana Özgü Dil Araçları Sözlüğü](/previous-versions/bb126564(v=vs.100))
- [Etki Alanına Özgü Dili Özelleştirme ve Genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md)