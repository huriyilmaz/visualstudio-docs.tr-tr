---
title: Yerelleştirme için kaynakların hiyerarşik organizasyonu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- resource files, localized
- localization [Visual Studio], resources
- fallback resources
- international applications [Visual Studio], storing resources
- satellite assemblies, resource hierarchies
- globalization [Visual Studio], resources
- satellite assemblies
- resources [Visual Studio], fallback system
- resource files, fallback processes
ms.assetid: dadf8f2c-f74c-44d7-bec0-a1e956d8d38d
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0a79caca18c7813605ff851eea6bda642e6300a0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645608"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Yerelleştirme için Kaynakların Hiyerarşik Organizasyonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da yerelleştirilmiş kaynaklar (her kültüre uygun dizeler ve görüntüler gibi veriler) ayrı dosyalarda depolanır ve Kullanıcı arabirimi kültürü ayarına göre yüklenir. Yerelleştirilmiş kaynakların nasıl yüklendiğini anlamak için, bunları hiyerarşik bir şekilde düzenlenmiş şekilde düşünmek yararlı olur.

## <a name="kinds-of-resources-in-the-hierarchy"></a>Hiyerarşideki kaynak türleri

- Hiyerarşinin en üstünde, varsayılan kültüre yönelik geri dönüş kaynakları (örneğin, Ingilizce ("en")). Bunlar, kendi dosyası olmayan tek kaynaklardır; Bunlar ana derlemede depolanırlar.

- Geri dönüş kaynaklarının altında, tüm nötr kültürler için kaynaklar bulunur. Nötr kültür bir dille ilişkilendirilir ancak ülke/bölge değildir. Örneğin, Fransızca ("fr") nötr bir kültür. (Geri dönüş kaynaklarının da bağımsız bir kültür için ve özel bir kültür için olduğunu unutmayın.)

- Belirli kültürlerin kaynakları aşağıda verilmiştir. Belirli bir kültür bir dil ve ülke/bölge ile ilişkilendirilir. Örneğin, Kanada Fransızcası ("fr-CA") belirli bir kültürdür.

  Bir uygulama, bir dize gibi yerelleştirilmiş bir kaynağı yüklemeye çalışırsa ve bunu bulamazsa, istenen kaynağı içeren bir kaynak dosyası bulana kadar hiyerarşiyi gezir.

  Kaynaklarınızı depolamanın en iyi yolu, bunları mümkün olduğunca genelleştirmenizi sağlar. Bu, mümkün olduğunda belirli kültürler yerine bağımsız kültürler için yerelleştirilmiş dizeleri, resimleri ve benzeri öğeleri depolar anlamına gelir. Örneğin, Fransızca Belçika ("fr-ın") kültürü için kaynaklarınız varsa ve yukarıdaki kaynaklar Ingilizce olarak geri dönüş kaynaklarındayken, birisi uygulamanızı Kanada Fransızcası için yapılandırılmış bir sistemde kullandığında bir sorun ortaya çıkabilir. Sistem, "fr-CA" için bir uydu derlemesini arar, bulamaz ve geri dönüş kaynağını içeren ana derlemeyi (Fransızca kaynakları yüklemek yerine Ingilizce) yükler. Aşağıdaki resimde bu istenmeyen senaryo gösterilmektedir.

  ![Yalnızca belirli kaynaklar](../ide/media/vbspecificresourcesonly.gif "yalnızca vbspecificresources")

  "Fr" kültürü için bağımsız bir kaynak dosyasında mümkün olduğunca çok kaynak yerleştirmeye yönelik önerilen uygulamayı izlerseniz, Kanada Fransızcası, "fr-to" kültürü için işaretlenmiş kaynakları görmez, ancak bu dize Fransızca olarak gösteriliyor. Aşağıdaki durum, tercih edilen bu senaryoyu göstermektedir.

  ![NeutralSpecificResources grafiği](../ide/media/vbneutralspecificresources.gif "vbNeutralSpecificResources")

## <a name="see-also"></a>Ayrıca Bkz.
 Yerelleştirme [güvenliği ve yerelleştirilmiş uydu derlemelerinin](../ide/security-and-localized-satellite-assemblies.md) [bağımsız kaynak dilleri](../ide/neutral-resources-languages-for-localization.md) [, uygulamaları](../ide/localizing-applications.md) [Genelleştirme ve yerelleştirme uygulamaları](../ide/globalizing-and-localizing-applications.md) Için [nasıl yapılır: Kültür ve Kullanıcı Arabirimi kültürünü Windows Forms ayarlama Genelleştirme](https://msdn.microsoft.com/694e049f-0b91-474a-9789-d35124f248f0) [nasıl yapılır: ASP.NET Web sayfası Genelleştirme için kültürü ve Kullanıcı Arabirimi kültürünü ayarlama](https://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0)
