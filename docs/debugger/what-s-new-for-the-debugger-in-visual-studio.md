---
title: Visual Studio 2017 ' de hata ayıklayıcıdaki yenilikler | Microsoft Docs
titleSuffix: ''
description: "Hata ayıklayıcı sürüm 15,5 ' deki yeni özelliklere bakın. Dahil: seçili ürün içi uygulamalar kodunun anlık görüntüleri ve IntelliTrace adım geri."
ms.custom: SEO-VS-2020
ms.date: 01/22/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 986ebf20cd49569bfcaf471b9bef994dfe774437
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149410"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Visual Studio 2017 ' de hata ayıklayıcıdaki yenilikler

Hata ayıklayıcı şu yeni özellikleri içerir:

- Sürüm 15,5 ' deki yenilikler **Snapshot Debugger** , çalışırken ilgilendiğiniz kod olduğunda üretim içi uygulamalarınızın anlık görüntüsünü alır. Hata ayıklayıcıya bir anlık görüntü almasını söylemek için kodunuzda anlık görüntü noktaları ve günlüğe kaydetme noktaları ayarlarsınız. Hata ayıklayıcı, üretim uygulamanızın trafiğini etkilemeden tam olarak neyin yanlış gittiğini görmenizi sağlar. Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için geçen süreyi önemli ölçüde düşürmeye yardımcı olabilir.

    Anlık görüntü koleksiyonu, Azure App Service çalıştıran aşağıdaki Web uygulamaları için kullanılabilir:

  * .NET Framework 4.6.1 veya sonraki sürümlerde çalışan uygulamalar ASP.NET.
  * .NET Core 2,0 veya üzeri sürümlerde çalışan uygulamaları Windows üzerinde ASP.NET Core.

    Daha fazla bilgi için bkz. [Snapshot Debugger kullanarak canlı ASP.NET uygulamalarında hata ayıklama](../debugger/debug-live-azure-applications.md).

- Sürüm 15,5 ' deki yenilikler yalnızca Visual Studio Enterprise sürümünde, **IntelliTrace adım geri** otomatik olarak her kesme noktası ve hata ayıklayıcı adım olayında uygulamanızın anlık görüntüsünü alır. Kaydedilen anlık görüntüler, önceki kesme noktalarına veya adımlara geri dönmenize ve uygulamanın geçmişte olduğu gibi durumunu görüntülemenize imkan tanır. IntelliTrace adım geri dönüş, önceki uygulama durumunu görmek istediğinizde, ancak hata ayıklamayı yeniden başlatmak veya istenen uygulama durumunu yeniden oluşturmak istemediğinizde size zaman kazandırabilir.

    Hata ayıklama araç çubuğundaki **geri** ve **adım ileri** düğmelerini kullanarak anlık görüntülerle gezinerek görüntüleyebilirsiniz. Bu düğmeler **Tanılama araçları** penceresindeki **Olaylar** sekmesinde görüntülenen olaylara gider.

    ![Geri adımla ve Ilet düğmeleri](../debugger/media/intellitrace-step-back-icons-description.png  "Geri adımla ve Ilet düğmeleri")

    Daha fazla bilgi için bkz. [IntelliTrace kullanarak önceki uygulama durumlarını İnceleme](view-historical-application-state.md) sayfası.

- **Özel** durum Yardımcısı özel durum yardımcısını değiştirir ve hatanın gerçekleştiği kalıcı olmayan bir iletişim kutusunda görünür. **Özel durum Yardımcısı** , tüm iç özel durumlara daha hızlı erişim sağlar, hata ayıklayıcı tarafından ek analizler (varsa) ve özel durum **ayarlarına** anında erişin. Özel durum Yardımcısı, görmeniz gereken bir şeyi engelliyorsa, bir kayan görünüme de sürüklenebilir.

    Örneğin, bir **NullReferenceException** artık null başvurusu olan değişkeni gösterir (ek bilgi).

    ![Hata ayıklayıcının özel durum Yardımcısı](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Daha fazla bilgi için bkz. [Visual Studio 'Da yeni özel durum yardımcısını kullanma](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/) blog gönderisi.

- Şimdi, **yürütmeyi buraya kadar Çalıştır** yeşil ok simgesine seçerek hata ayıklayıcıda duraklayana bir kod satırına çalıştırabilirsiniz (bir kod satırının üzerine gelindiğinde simgeyi görürsünüz). Bu, geçici kesme noktaları ayarlama gereksinimini ortadan kaldırır.

    ![Hata ayıklayıcının tıklama için Çalıştır](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- Özel durum **ayarları** iletişim kutusunda özel durumlar için koşullar ayarlayabilirsiniz (özel durum ayarları iletişim kutusundaki **koşulu Düzenle** simgesini veya özel durum üzerinde sağ tıklama menüsünü kullanarak bunu yapabilirsiniz.) Şu anda desteklenen koşullar, özel durum için dahil edilecek veya hariç tutulacak modül adlarını içerir.

    ![Özel durum koşulları](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- Işleme İliştir iletişim kutusu, iliştirilebilmeniz gereken işlemi daha hızlı tanımanıza yardımcı olabilecek yeni bir arama özelliği içerir.

    ![Işleme Iliştir içinde ara](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Bu yeni özellikler hakkında daha fazla bilgi için [sürüm notlarına [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)