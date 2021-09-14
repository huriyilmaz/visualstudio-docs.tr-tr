---
title: Domain-Specific dil Araçları Kullanıcı arabirimine genel bakış
description: Visual Studio ' de alana özgü dil Araçları çözümünün Kullanıcı arabirimine genel bir bakış sağlar.
ms.date: 11/04/2016
ms.topic: overview
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 7e5eadf964f8809c10a4a7b6654397b7ebb9b4f1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637609"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Etki Alanına Özgü Dil Araçları Kullanıcı Arabirimine Genel Bakış
Visual Studio Domain-Specific dil araçları (DSL araçları) çözümünü ilk kez açtığınızda, kullanıcı arabirimi aşağıdaki resme benzeyecektir.

 ![DSL Tasarımcısı](../modeling/media/dsl_designer.png)

 Aşağıdaki tabloda, Kullanıcı arabiriminin bölümlerinin nasıl kullanıldığı açıklanmaktadır.

|**Öğe**|**Tanım**|
|-|-|
|Diyagram|Diyagram, etki alanı modelini görüntüler.<br /><br /> Diyagramda iki kenar vardır. Bir taraf modellerinizde öğelerin türlerini tanımlar. Diğer kenar, modellerinizin ekranda nasıl görüneceğini tanımlar.|
|Araç Kutusu|Diyagrama etki alanı sınıfları ve şekil türleri eklemek için araç kutusundan Araçlar ' a sürükleyin. İlişkiler, bağlayıcılar ve şekil haritaları eklemek için araca tıklayın, ardından diyagramdaki kaynak düğümüne ve ardından hedef düğüme tıklayın.|
|DSL Gezgini|DSL **Gezgini** , bir DSL tanımı etkin pencere olduğunda görüntülenir. DSL 'yi ağaç olarak gösterir. DSL Gezgini, modelin diyagramda görüntülenmeyen özelliklerini düzenlemenize olanak tanır. Örneğin, **DSL Gezginini** kullanarak araç kutusu öğelerini ve doğrulama işlemine geçiş yapabilirsiniz.|
|DSL ayrıntıları penceresi|**DSL ayrıntıları** penceresi, öğelerin nasıl görüntülendiğini ve öğelerin nasıl kopyalanıp silineceğini denetlemenizi sağlayan etki alanı modelinin öğelerinin özelliklerini gösterir.<br /><br /> -Varsayılan olarak, **hata listesi** ve **Çıkış** pencerelerinin yanında **DSL ayrıntıları** penceresi görünür.|

## <a name="the-domain-model-diagram"></a>Etki alanı modeli diyagramı
 Etki alanı modeli diyagramı iki parçaya ayrılmıştır. Diyagramın bir tarafı modeldeki öğeleri ve ilişkileri gösterir. Diğer tarafta modelin nasıl görüntüleneceği gösterilir ve öğe ve model diyagramının özelliklerini göstermek için kullanılan şekiller bulunur. Aşağıdaki resimde diyagramın öğeleri gösterilmektedir.

 ![Kulvar ile DSL Tasarımcısı](../modeling/media/dsl_desinger.png)

 Aşağıdaki tabloda, etki alanı modeli diyagramının bazı öğeleri açıklanmaktadır.

|**Süre**|**Tanım**|
|-|-|
|Alan sınıfı|Etki alanı sınıfları, modellerinizde bulunan öğelerin türleridir.<br /><br /> Bir etki alanı sınıfı, birden fazla ilişkinin hedefi ise diyagramda birden çok kez görünebilir.<br /><br /> Bir etki alanı sınıfı eklemek için, etki alanı sınıfı aracını **araç kutusundan** diyagramın **sınıflar ve ilişkiler** tarafına sürükleyin.|
|Etki alanı Ilişkisi|Etki alanı ilişkileri, modellerinizde bulunan öğeler arasındaki bağlantı türleridir.<br /><br /> Bir *katıştırma ilişkisi* , hedef öğenin sahip olduğunu veya kaynak öğe tarafından içerildiğini ve düz bir çizgi olarak göründüğünü gösterir. Modeldeki her öğe tek bir katıştırma ilişkisinin hedefi olmalıdır, böylece model bir ağaç oluşturur. *Başvuru ilişkisi* , model öğeleri arasındaki genel bağlantıyı gösterir ve kesik çizgili bir çizgi olarak görünür. Herhangi bir öğe herhangi bir sayıda başvuru bağlantısına sahip olabilir.<br /><br /> **Araç kutusundaki** araca tıklayıp kaynak etki alanı sınıfına ve ardından hedef sınıfa tıklayarak bir ilişki oluşturun.|
|Şekiller ve bağlayıcılar|Şekiller, model öğelerinin bir DSL diyagramında nasıl görüntüleneceğini belirtir. bağlayıcılar, ilişkileri göstermek için kullanılabilecek bir DSL diyagramında çizgiler belirler.<br /><br /> Bir şekil veya bağlayıcı oluşturmak için, aracı diyagram **öğeleri** tarafına sürükleyin.|
|şekil Haritalar|Şekil eşlemesi, etki alanı modeli diyagramında bir çizgi olarak görünür, bir şekli görüntülediği etki alanı sınıfına ya da görüntülediği etki alanı ilişkisine bir bağlayıcı ile bağlantılandırın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Etki Alanına Özgü Dil Araçlarına Genel Bakış](../modeling/overview-of-domain-specific-language-tools.md)
- [Alana Özgü Dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))
- [Etki Alanına Özgü Dili Özelleştirme ve Genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md)