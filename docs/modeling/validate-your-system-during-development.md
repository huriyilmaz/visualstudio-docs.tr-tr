---
title: Geliştirme sırasında sisteminizi doğrulama
description: Yazılımlarınızı Visual Studio gereksinimleriyle ve sisteminizin mimarisiyle tutarlı tutmaya nasıl yardımcı olduğunu öğrenin.
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
ms.openlocfilehash: f33e24c9284a785eeef2ba87d9f63855fc4d9c8259f6adc6ac44d1090a85dc34
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121398079"
---
# <a name="validate-your-system-during-development"></a>Geliştirme sırasında sisteminizi doğrulama

Visual Studio, yazılımlarınızı kullanıcı gereksinimleriyle ve sisteminizin mimarisiyle tutarlı tutmaya yardımcı olabilir.

Bu özelliklerin hangi sürümlerinin Visual Studio desteklemektedir, bkz. [Mimari ve modelleme araçları için sürüm desteği.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="key-tasks"></a>Önemli Görevler

Yazılımınızı doğrulamak için aşağıdaki görevleri kullanın:

|**Görevler**|**İlişkili Konular**|
|-|-|
|**Yazılımınız kullanıcıların gereksinimlerini karşılar:**<br /><br />Sistem ve bileşenlerinin testlerini düzenlemenize yardımcı olmak için gereksinimleri ve mimari modelleri kullanın. Bu uygulama, kullanıcılar ve diğer paydaşlar için önemli olan gereksinimleri test etmenizi sağlar ve gereksinimler değiştiklerinde testleri hızla güncelleştirmenizi sağlar.|- [Modelden test geliştirme](../modeling/develop-tests-from-a-model.md)|
|**Yazılımınızı, sisteminizin hedeflenen tasarımıyla tutarlı olduğundan emin olun:**<br /><br />Bağımlılık diyagramları, uygulama bileşenleri arasındaki hedeflenen bağımlılıkları açıklar. Geliştirme sırasında, kodda gerçek bağımlılıkların hedeflenen tasarıma uygun olduğunu doğrularsiniz.|- [Kodunuzdan bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık diyagramları ile kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Dış Kaynaklar

|**Kategori**|**Bağlantılar**|
|-|-|
|**Videolar**|![Channel 9 video ](../data-tools/media/playvideo.gif) [bağlantısı: Doug Seven: Code Understanding and Systems Design with Visual Studio 2010](https://channel9.msdn.com/shows/VS2010Launch/Doug-Seven-Code-Understanding-and-Systems-Design-with-Visual-Studio-2010)<br /><br /> ![video bağlantısı ](../data-tools/media/playvideo.gif) [Channel 9: Architecting an Application](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-5-architecting-an-application))|
|**Forumlar**|- [Visual Studio Görselleştirme & Modelleme Araçları](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio genişletilebilirliği](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx)|

## <a name="see-also"></a>Ayrıca bkz.

- [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)
- [Mimariyi analiz etme ve modelleme](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
