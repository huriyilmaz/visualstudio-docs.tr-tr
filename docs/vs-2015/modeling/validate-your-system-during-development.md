---
title: Geliştirme sırasında sisteminizi doğrulama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4fec3595ba7886f5ba979c35e9441ab108174726
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301337"
---
# <a name="validate-your-system-during-development"></a>Geliştirme sırasında sisteminizi doğrulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio, yazılımınızın kullanıcıların gereksinimleriyle ve sisteminizin mimarisiyle tutarlı kalmasına yardımcı olabilir.

 Visual Studio 'nun hangi sürümlerinin bu özelliklerden her birini desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Anahtar görevler
 Yazılımınızı doğrulamak için aşağıdaki görevleri kullanın.

|**Görevler**|**İlişkili konular**|
|---------------|---------------------------|
|**Modelinizin tutarlı olduğundan emin olun:**<br /><br /> Projenizin kullanma ve modelleri yorumlama yönteminize bağlı olarak, bazı öğe birleşimlerine izin vermemek faydalı olabilir. Örneğin, UML sınıflarını, her zaman [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]uyumlu adlara sahip olacak şekilde kısıtlayabilirsiniz. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzantılarında bu gibi kısıtlamalar tanımlayabilirsiniz.|[UML modelinizi doğrulamak](../modeling/validate-your-uml-model.md) -   <br />[UML modelleri için doğrulama kısıtlamalarını tanımlama](../modeling/define-validation-constraints-for-uml-models.md) -   |
|**Yazılımınızın kullanıcıların gereksinimlerini karşıladığından emin olun**:<br /><br /> Sistem ve bileşenlerinin testlerini düzenlemenize yardımcı olması için gereksinimleri ve mimari modelleri kullanabilirsiniz. Bu uygulama, kullanıcılar ve diğer paydaşlar için önemli olan gereksinimleri test etmenize yardımcı olur ve gereksinimler değiştiğinde testleri hızlı bir şekilde güncelleştirmenize yardımcı olur.|-   [bir modelden test geliştirme](../modeling/develop-tests-from-a-model.md)|
|**Yazılımınızın sisteminizin tasarlanan tasarımla tutarlı kaldığından emin olun:**<br /><br /> Katman diyagramları, uygulamanızın bileşenleri arasındaki amaçlanan bağımlılıkları anlatmaktadır. Geliştirme sırasında, koddaki gerçek bağımlılıkların amaçlanan tasarıma uygun olduğunu doğrulayabilirsiniz.|-   [kodunuzda katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />[Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md) -   |

## <a name="external-resources"></a>Dış Kaynaklar

|**Kategori**|**Köprü**|
|------------------|---------------|
|**Videolar**|![video](../data-tools/media/playvideo.gif "PlayVideo") [kanalı 9 ' a bağlantı: Doug yedi: Visual Studio 2010 ile kod anlama ve sistem tasarımı](https://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![video](../data-tools/media/playvideo.gif "PlayVideo ") [kanalı 9 ' a bağlantı: katman diyagramı kullanarak uygulama mimarisi](https://go.microsoft.com/fwlink/?LinkID=201117) oluşturma<br /><br /> ![video MSDN 'ye bağlantı](../data-tools/media/playvideo.gif "PlayVideo ") [: nasıl yapılır serisi: Katman diyagramlarını kullanarak kodu doğrulama](https://go.microsoft.com/fwlink/?LinkID=214405)|
|**Forumları**|-   [Visual Studio görselleştirme & modelleme araçları](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio görselleştirme & modelleme SDK (dsl araçları)](https://go.microsoft.com/fwlink/?LinkId=184721)|
|**Bloglar**|-   [Visual STUDIO ALM + Team Foundation Server blogu](https://go.microsoft.com/fwlink/?LinkID=201340)|
|**Teknik makaleler ve Günlükler**|[MSDN mimari Merkezi](https://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>Ayrıca Bkz.
 [Uygulamayı test etme](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [UML modellerini ve Diyagramları Genişletme](../modeling/extend-uml-models-and-diagrams.md) [Kullanıcı gereksinimleri](../modeling/model-user-requirements.md) [çözümleme ve modelleme mimarisi](../modeling/analyze-and-model-your-architecture.md)
