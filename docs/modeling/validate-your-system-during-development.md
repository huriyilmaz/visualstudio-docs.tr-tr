---
title: Geliştirme sırasında sisteminizi doğrulama
description: Visual Studio, yazılımınızın kullanıcı gereksinimleriyle ve sisteminizin mimarisiyle tutarlı tutulmasına nasıl yardımcı olabileceğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 4a11c41b76bff61ed5af0916f0d43aa5739da78a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116558"
---
# <a name="validate-your-system-during-development"></a>Geliştirme sırasında sisteminizi doğrulama

Visual Studio, yazılımınızın kullanıcı gereksinimleriyle ve sisteminizin mimarisiyle tutarlı kalmasına yardımcı olabilir.

hangi Visual Studio sürümlerinin bu özelliklerden her birini desteklediğini görmek için bkz. [mimari ve modelleme araçları için sürüm desteği](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

## <a name="key-tasks"></a>Anahtar görevler

Yazılımınızı doğrulamak için aşağıdaki görevleri kullanın:

|**Görevler**|**İlişkili Konular**|
|-|-|
|**Yazılımınızın kullanıcıların gereksinimlerini karşıladığından emin olun**:<br /><br />Sisteminizin ve bileşenlerinin testlerini düzenlemenize yardımcı olması için gereksinimleri ve mimari modellerini kullanın. Bu uygulama, kullanıcılar ve diğer paydaşlar için önemli olan gereksinimleri test etmenize yardımcı olur ve gereksinimler değiştiğinde testleri hızlı bir şekilde güncelleştirmenize yardımcı olur.|- [Bir modelden testler geliştirme](../modeling/develop-tests-from-a-model.md)|
|**Yazılımınızın sisteminizin tasarlanan tasarımla tutarlı kaldığından emin olun:**<br /><br />Bağımlılık diyagramları, uygulamanızın bileşenleri arasındaki amaçlanan bağımlılıkları anlatmaktadır. Geliştirme sırasında, koddaki gerçek bağımlılıkların amaçlanan tasarıma uygun olduğunu doğrulayabilirsiniz.|- [Kodunuzda bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık diyagramları ile kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Dış Kaynaklar

|**Kategori**|**Bağlantılar**|
|-|-|
|**Videolar**|![video ](../data-tools/media/playvideo.gif) [kanalı 9 ' a bağlantı: doug yedi: Visual Studio 2010 ile kod anlama ve sistem tasarımı](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![video kanalı 9 ' a bağlantı ](../data-tools/media/playvideo.gif) [: uygulama mimarisi oluşturma](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application)|
|**Forumlar**|- [Visual Studio Görselleştirme & modelleme araçları](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio genişletilebilirlik](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>Ayrıca bkz.

- [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)
- [Analiz ve model mimarisi](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
