---
title: Visual Studio 2017'de Hata Ayıklayıcısı | Microsoft Docs
titleSuffix: ''
description: "Hata ayıklayıcısı sürüm 15.5'te yeni özelliklere bakın. Dahil edilenler: Üretim içi uygulamaların seçili kodunun anlık görüntüleri ve Intellitrace geri adımı."
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 7a743d43459e124d2377339a57756d8c0410a344
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112275"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2017"></a>Visual Studio 2017'de Hata Ayıklayıcısı'nın Visual Studio

Hata ayıklayıcısı şu yeni özellikleri içerir:

- Sürüm 15.5'te yeni **olan Snapshot Debugger,** ilgilendiğiniz kod yürütülürken üretim uygulamalarınıza bir anlık görüntü alır. Hata ayıklayıcıya anlık görüntü alma talimatı almak için kodunda anlık görüntü noktaları ve günlük noktaları ayarlayın. Hata ayıklayıcısı, üretim uygulama trafiğinizi etkilemeden tam olarak neyin yanlış gittiğini görmenizi sağlar. Bu Snapshot Debugger, üretim ortamlarında oluşan sorunları çözmek için gereken zamanı önemli ölçüde azaltmanıza yardımcı olabilir.

    Anlık görüntü koleksiyonu, aşağıdaki web uygulamaları için kullanılabilir ve Azure App Service:

  * ASP.NET 4.6.1 veya .NET Framework üzerinde çalışan uygulamalar.
  * ASP.NET Core .NET Core 2.0 veya sonraki bir üzerinde çalışan uygulamaları Windows.

    Daha fazla bilgi için [bkz. ASP.NET kullanarak canlı Snapshot Debugger.](../debugger/debug-live-azure-applications.md)

- Yalnızca 15.5 sürümünde yeni Visual Studio Enterprise **IntelliTrace** geri adımı, her kesme noktası ve hata ayıklayıcısı adım olayında otomatik olarak uygulamanın anlık görüntüsünü alır. Kaydedilen anlık görüntüler, önceki kesme noktalarına veya adımlara geri dönmenizin yanı sıra uygulamanın geçmişte olduğu gibi durumunu görüntülemeye olanak sağlar. IntelliTrace geri adımı önceki uygulama durumunu görmek istediğiniz ancak hata ayıklamayı yeniden başlatmak veya istenen uygulama durumunu yeniden oluşturmak istemeyebilirsiniz.

    Hata Ayıklama araç çubuğundaki Geri Adım ve İleri **Adım** düğmelerini **kullanarak** anlık görüntülerde gezinebilirsiniz ve görüntüleyebilirsiniz. Bu düğmeler, Tanılama Araçları **penceresindeki** Olaylar **sekmesinde görünen Tanılama Araçları** gezinebilirsiniz.

    ![Geri ve İleri Adım Düğmeleri](../debugger/media/intellitrace-step-back-icons-description.png  "Geri ve İleri Adım düğmeleri")

    Daha fazla bilgi için [IntelliTrace kullanarak önceki uygulama eyaletlerini inceleme sayfasına](view-historical-application-state.md) bakın.

- Özel **Durum Yardımcısı,** Özel Durum Yardımcısı'nın yerini alır ve hatanın meydana geldiği kalıcı olmayan bir iletişim kutusunda görünür. Özel **Durum Yardımcısı herhangi** bir iç özel durum için daha hızlı erişim, hata ayıklayıcı tarafından ek analiz (varsa) ve özel durum için Özel Durum Ayarlar erişim sağlar.  Özel Durum Yardımcı, görmen gereken bir şeyi engelliyorsa kayan görünüme de sürüklenerek.

    Örneğin, **NullReferenceException** artık null başvurusu olan değişkeni gösterir (ek bilgi).

    ![Hata Ayıklayıcısının Özel Durum Yardımcısı](../debugger/media/dbg-exception-helper.png "DbgExceptionHelper")

    Daha fazla bilgi için Visual Studio blog gönderisinde [Yeni Özel Durum Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/) bakın.

- Artık Yürütmeyi buraya kadar çalıştır yeşil ok simgesini seçerek  hata ayıklayıcıda duraklatılmış bir kod satırına çalıştırabilirsiniz (bir kod çizgisinin üzerine gelindiğinde simgeyi görüyorsunuz). Bu, geçici kesme noktaları ayarlama ihtiyacının ortadan kaldırılmasını sağlar.

    ![Hata Ayıklayıcının Tıklamak için Çalıştır](../debugger/media/dbg-run-to-click.png "DbgRunToClick")

- Özel durumlarla ilgili koşulları Özel **Durum Ayarlar** iletişim kutusunda ayarlayabilirsiniz (Özel  Durum Ayarlar iletişim kutusundaki Koşulu düzenle simgesini kullanarak veya özel durumda sağ tıklama menüsünü kullanarak bunu yapabilirsiniz.) Şu anda desteklenen koşullar, özel durum için dahil etmek veya hariç tutmak için modül adlarını içerir.

    ![Özel Durum Koşulları](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

- İşleme Ekle iletişim kutusu, iliştirmek istediğiniz işlemi daha hızlı tanımlamanıza yardımcı olacak yeni bir arama özelliği içerir.

    ![İşleme Ekle içinde arama](../debugger/media/dbg-attach-to-process-search.png "DbgAttachToProcessSearch")

Bu yeni özellikler hakkında daha fazla bilgi için bkz. [sürüm notları. [!include[vs_dev15](../misc/includes/vs_dev15_md.md)] ](/visualstudio/releasenotes/vs2017-relnotes)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)