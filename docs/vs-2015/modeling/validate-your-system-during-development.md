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
ms.openlocfilehash: b3de5cb1cc62d159567eee804c1aadef865e500a
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75845390"
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

|**Kategori**|**Bağlantılar**|
|------------------|---------------|
|**Videolar**|![video](../data-tools/media/playvideo.gif "PlayVideo") [kanalı 9 ' a bağlantı: Doug yedi: Visual Studio 2010 ile kod anlama ve sistem tasarımı](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![video](../data-tools/media/playvideo.gif "PlayVideo") [kanalı 9 ' a bağlantı: katman diyagramı kullanarak uygulama mimarisi](https://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-5-Architecting-an-Application) oluşturma<br /><br /> ![video MSDN 'ye bağlantı](../data-tools/media/playvideo.gif "PlayVideo") [: nasıl yapılır serisi: Katman diyagramlarını kullanarak kodu doğrulama](https://msdn.microsoft.com/vstudio/gg501755)|
|**Forumlar**|-   [Visual Studio görselleştirme & modelleme araçları](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio görselleştirme & modelleme SDK (dsl araçları)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Bloglar**|-   [Visual STUDIO ALM + Team Foundation Server blogu](https://blogs.msdn.com/b/visualstudioalm)|
|**Teknik makaleler ve Günlükler**|[MSDN mimari Merkezi](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Ayrıca Bkz.
 [Uygulamayı test etme](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [UML modellerini ve Diyagramları Genişletme](../modeling/extend-uml-models-and-diagrams.md) [Kullanıcı gereksinimleri](../modeling/model-user-requirements.md) [çözümleme ve modelleme mimarisi](../modeling/analyze-and-model-your-architecture.md)
