---
title: Geliştirme sırasında sisteminizi doğrulama
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 328b600a21adf274d1d016f595438eb5622ee853
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663741"
---
# <a name="validate-your-system-during-development"></a>Geliştirme sırasında sisteminizi doğrulama

Visual Studio, yazılımınızın Kullanıcı gereksinimleriyle ve sisteminizin mimarisiyle tutarlılığını sağlamanıza yardımcı olabilir.

Visual Studio 'nun hangi sürümlerinin bu özelliklerden her birini desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Anahtar görevler

Yazılımınızı doğrulamak için aşağıdaki görevleri kullanın:

|**Görevler**|**İlişkili konular**|
|-|-|
|**Yazılımınızın kullanıcıların gereksinimlerini karşıladığından emin olun**:<br /><br />Sisteminizin ve bileşenlerinin testlerini düzenlemenize yardımcı olması için gereksinimleri ve mimari modellerini kullanın. Bu uygulama, kullanıcılar ve diğer paydaşlar için önemli olan gereksinimleri test etmenize yardımcı olur ve gereksinimler değiştiğinde testleri hızlı bir şekilde güncelleştirmenize yardımcı olur.|- [bir modelden test geliştirme](../modeling/develop-tests-from-a-model.md)|
|**Yazılımınızın sisteminizin tasarlanan tasarımla tutarlı kaldığından emin olun:**<br /><br />Bağımlılık diyagramları, uygulamanızın bileşenleri arasındaki amaçlanan bağımlılıkları anlatmaktadır. Geliştirme sırasında, koddaki gerçek bağımlılıkların amaçlanan tasarıma uygun olduğunu doğrulayabilirsiniz.|- [kodınızdan bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />[bağımlılık diyagramlarında kodu doğrulamak](../modeling/validate-code-with-layer-diagrams.md) - |

## <a name="external-resources"></a>Dış Kaynaklar

|**Alan**|**Köprü**|
|-|-|
|**Videolar**|![link video ](../data-tools/media/playvideo.gif) [Kanal 9: Doug yedi: Visual Studio 2010 Ile kod anlama ve sistem tasarımı](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![link video ](../data-tools/media/playvideo.gif) [Channel 9: uygulama mimarisi](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application))|
|**Forumları**|- [Visual Studio görselleştirme & modelleme araçları](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />[Visual Studio genişletilebilirliği](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) - |

## <a name="see-also"></a>Ayrıca bkz.

- [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)
- [Analiz ve model mimarisi](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
