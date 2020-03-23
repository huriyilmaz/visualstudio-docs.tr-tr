---
title: Etki Alanına Özgü Dil Araçları Kullanıcı Arabirimine Genel Bakış | Microsoft Dokümanlar
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "72652130"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Etki Alanına Özgü Dil Araçları Kullanıcı Arabirimine Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Etki Alanına Özgü Dil Araçları (DSL Tools) [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]çözümlerini ilk açtığınızda, kullanıcı arabirimi aşağıdaki resme benzeyecektir.

 ![dsl tasarımcısı](../modeling/media/dsl-designer.png "dsl_designer")

 Aşağıdaki tabloda, UI'nin bölümlerinin nasıl kullanıldığı açıklanmaktadır.

|**Öğe**|**Tanım**|
|-----------------|--------------------|
|Diyagram|Diyagram etki alanı modelini görüntüler.<br /><br /> Diyagramın iki tarafı vardır. Bir taraf modellerinizdeki öğelerin türlerini tanımlar. Diğer taraf, modellerinizin ekranda nasıl görüneceğini tanımlar.|
|Araç Kutusu|Diyagrama etki alanı sınıfları ve şekil türleri eklemek için araçları araç kutusundan sürükleyin. İlişkiler, bağlayıcılar ve şekil eşlemleri eklemek için aracı tıklatın, ardından diyagramdaki kaynak düğümünü ve ardından hedef düğümü tıklatın.|
|DSL Gezgini|**DSL** tanımı etkin pencere olduğunda DSL Explorer görüntülenir. DSL'yi ağaç olarak gösterir. DSL Explorer, diyagramda görüntülenmeyen modelin özelliklerini düzenlemenize olanak tanır. Örneğin, **dsl explorer**kullanarak araç kutusu öğeleri ekleyebilir ve doğrulama işlemini açabilirsiniz.|
|DSL Ayrıntılar penceresi|**DSL Ayrıntılar** penceresi, etki alanı modelinin öğelerinin öğelerinin nasıl görüntüleneceğini ve öğelerin nasıl kopyalanıp silindiğini denetlemenize olanak tanıyan özelliklerini gösterir.<br /><br /> - Varsayılan olarak, **DSL Ayrıntılar** penceresi **Hata Listesi** ve **Çıktı** pencerelerinin yanında görünür.|

## <a name="the-domain-model-diagram"></a>Etki Alanı Modeli Diyagramı
 Etki alanı modeli diyagramı iki bölüme ayrılmıştır. Diyagramın bir tarafı modeldeki öğeleri ve ilişkileri gösterir. Diğer taraf, modelin nasıl görüntüleneceğini gösterir ve model diyagramının öğelerini ve özelliklerini görüntülemek için kullanılan şekilleri içerir. Aşağıdaki resimde diyagramın öğeleri gösterilmektedir.

 ![kulvarlı dsl tasarımcısı](../modeling/media/dsl-desinger.png "dsl_desinger")

 Aşağıdaki tabloda etki alanı modeli diyagramının bazı öğeleri açıklanmaktadır.

|**Terim**|**Tanım**|
|--------------|--------------------|
|Etki Alanı Sınıfı|Etki alanı sınıfları modellerinizdeki öğe türleridir.<br /><br /> Etki alanı sınıfı, birden fazla ilişkinin hedefiyse, diyagramda birden fazla kez görünebilir.<br /><br /> Etki alanı sınıfı eklemek için etki alanı sınıfı aracını **Araç Kutusu'ndan** diyagramın **Sınıflar ve İlişkiler** tarafına sürükleyin.|
|Etki Alanı İlişkisi|Etki alanı ilişkileri, modellerinizdeki öğeler arasındaki bağlantı türleridir.<br /><br /> *Katıştırma ilişkisi,* hedef öğenin kaynak öğeye sahip olduğunu veya içerdiğini gösterir ve düz bir çizgi olarak görünür. Bir modeldeki her öğe, bir katıştırma ilişkisinin hedefi olmalıdır, böylece model bir ağaç oluşturur. *Başvuru ilişkisi* model öğeleri arasında genel bir bağlantı gösterir ve kesik çizgi olarak görünür. Herhangi bir öğenin herhangi bir sayıda referans bağlantısı olabilir.<br /><br /> **Araç Kutusu'ndaki**aracı tıklatarak, kaynak etki alanı sınıfını tıklatarak ve ardından hedef sınıfı tıklatarak bir ilişki oluşturun.|
|Şekiller ve Bağlayıcılar|Şekiller, model öğelerinin DSL diyagramında nasıl görüntüleneceğini belirtir., Bağlayıcılar ilişkileri görüntülemek için kullanılabilecek bir DSL diyagramında çizgiler belirtir.<br /><br /> Bir şekil veya bağlayıcı oluşturmak için aracı diyagramın **Diyagram Öğeleri** tarafına sürükleyin.|
|Şekil Haritaları|Şekil eşlemi, etki alanı modeli diyagramında bir çizgi olarak görünür ve bir şekli görüntülenebilen etki alanı sınıfına veya görüntülenedeki etki alanı ilişkisine bağlayıcı olarak görünür.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Etki Alanına Özgü Dil Araçlarına Genel Bakış](../modeling/overview-of-domain-specific-language-tools.md) [Etki Alanına Özgü Dil Araçları Sözlüğü Etki](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) Alanına Özgü Bir Dili Özelleştirme ve [Genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md)
