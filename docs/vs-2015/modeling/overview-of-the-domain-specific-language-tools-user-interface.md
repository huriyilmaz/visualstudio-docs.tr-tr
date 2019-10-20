---
title: Alana Özgü Dil Araçları Kullanıcı arabirimine genel bakış | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: overview
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
ms.assetid: 81ae6b35-6819-41d0-953b-6b4ed81f9227
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3bffb1f7fe6449f078c21c14b0a070cbd23db539
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652130"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Etki Alanına Özgü Dil Araçları Kullanıcı Arabirimine Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

@No__t_0 bir Alana Özgü Dil Araçları (DSL araçları) çözümünü ilk kez açtığınızda, Kullanıcı arabirimi aşağıdaki resme benzeyecektir.

 ![DSL Tasarımcısı](../modeling/media/dsl-designer.png "dsl_designer")

 Aşağıdaki tabloda, Kullanıcı arabiriminin bölümlerinin nasıl kullanıldığı açıklanmaktadır.

|**Öğe**|**Tanım**|
|-----------------|--------------------|
|Diyagram|Diyagram, etki alanı modelini görüntüler.<br /><br /> Diyagramda iki kenar vardır. Bir taraf modellerinizde öğelerin türlerini tanımlar. Diğer kenar, modellerinizin ekranda nasıl görüneceğini tanımlar.|
|Araç Kutusu|Diyagrama etki alanı sınıfları ve şekil türleri eklemek için araç kutusundan Araçlar ' a sürükleyin. İlişkiler, bağlayıcılar ve şekil haritaları eklemek için araca tıklayın, ardından diyagramdaki kaynak düğümüne ve ardından hedef düğüme tıklayın.|
|DSL Gezgini|DSL **Gezgini** , bir DSL tanımı etkin pencere olduğunda görüntülenir. DSL 'yi ağaç olarak gösterir. DSL Gezgini, modelin diyagramda görüntülenmeyen özelliklerini düzenlemenize olanak tanır. Örneğin, **DSL Gezginini**kullanarak araç kutusu öğelerini ve doğrulama işlemine geçiş yapabilirsiniz.|
|DSL ayrıntıları penceresi|**DSL ayrıntıları** penceresi, öğelerin nasıl görüntülendiğini ve öğelerin nasıl kopyalanıp silineceğini denetlemenizi sağlayan etki alanı modelinin öğelerinin özelliklerini gösterir.<br /><br /> -Varsayılan olarak, **hata listesi** ve **Çıkış** pencerelerinin yanında **DSL ayrıntıları** penceresi görünür.|

## <a name="the-domain-model-diagram"></a>Etki alanı modeli diyagramı
 Etki alanı modeli diyagramı iki parçaya ayrılmıştır. Diyagramın bir tarafı modeldeki öğeleri ve ilişkileri gösterir. Diğer tarafta modelin nasıl görüntüleneceği gösterilir ve öğe ve model diyagramının özelliklerini göstermek için kullanılan şekiller bulunur. Aşağıdaki resimde diyagramın öğeleri gösterilmektedir.

 ![Kulvar ile DSL Tasarımcısı](../modeling/media/dsl-desinger.png "dsl_desinger")

 Aşağıdaki tabloda, etki alanı modeli diyagramının bazı öğeleri açıklanmaktadır.

|**Terimli**|**Tanım**|
|--------------|--------------------|
|Alan sınıfı|Etki alanı sınıfları, modellerinizde bulunan öğelerin türleridir.<br /><br /> Bir etki alanı sınıfı, birden fazla ilişkinin hedefi ise diyagramda birden çok kez görünebilir.<br /><br /> Bir etki alanı sınıfı eklemek için, etki alanı sınıfı aracını **araç kutusundan** diyagramın **sınıflar ve ilişkiler** tarafına sürükleyin.|
|Etki alanı Ilişkisi|Etki alanı ilişkileri, modellerinizde bulunan öğeler arasındaki bağlantı türleridir.<br /><br /> Bir *katıştırma ilişkisi* , hedef öğenin sahip olduğunu veya kaynak öğe tarafından içerildiğini ve düz bir çizgi olarak göründüğünü gösterir. Modeldeki her öğe tek bir katıştırma ilişkisinin hedefi olmalıdır, böylece model bir ağaç oluşturur. *Başvuru ilişkisi* , model öğeleri arasındaki genel bağlantıyı gösterir ve kesik çizgili bir çizgi olarak görünür. Herhangi bir öğe herhangi bir sayıda başvuru bağlantısına sahip olabilir.<br /><br /> **Araç kutusundaki**araca tıklayıp kaynak etki alanı sınıfına ve ardından hedef sınıfa tıklayarak bir ilişki oluşturun.|
|Şekiller ve bağlayıcılar|Şekiller, model öğelerinin bir DSL diyagramında nasıl görüntüleneceğini belirtir. bağlayıcılar, ilişkileri göstermek için kullanılabilecek bir DSL diyagramında çizgiler belirler.<br /><br /> Bir şekil veya bağlayıcı oluşturmak için, aracı diyagram **öğeleri** tarafına sürükleyin.|
|Şekil haritaları|Şekil eşlemesi, etki alanı modeli diyagramında bir çizgi olarak görünür, bir şekli görüntülediği etki alanı sınıfına ya da görüntülediği etki alanı ilişkisine bir bağlayıcı ile bağlantılandırın.|

## <a name="see-also"></a>Ayrıca Bkz.
 Alana Özgü Dil Araçları [alana özgü dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) ['Ne genel bakış](../modeling/overview-of-domain-specific-language-tools.md) [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md)
