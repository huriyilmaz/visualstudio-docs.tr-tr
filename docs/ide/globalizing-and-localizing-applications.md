---
title: Yerelleştirme araçları
description: Visual Studio'ye dahil edilen yerelleştirme araçlarını ve bunları birden çok dilde yerelleştirilmiş uygulamalar oluşturmak için nasıl kullanabileceğiniz hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 02/15/2019
ms.topic: reference
helpviewer_keywords:
- globalization [Visual Studio]
- Visual Basic code, international applications
- C#, international applications
- localization [Visual Studio]
- world-ready applications
- international applications [Visual Studio]
ms.assetid: 4d9815ae-3e80-4b4d-933d-f8309aee18d5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 4411ab1280bc8c39fcbf49a5ee80f1722a84d1d5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086163"
---
# <a name="develop-globalized-and-localized-apps"></a>Genelleştirilmiş ve yerelleştirilmiş uygulamalar geliştirme

Visual Studio. .NET'e yerleşik hizmetlerden faydalanarak uluslararası bir hedef kitle için [geliştirmeyi kolaylaştırır.](/dotnet/standard/globalization-localization/)

Örneğin, Windows Forms uygulamaları için proje sistemi, hem geri dönüş kullanıcı arabirimi kültürü hem de ek ui kültürü için kaynak dosyaları oluşturur. Visual Studio'de bir proje derlemeniz, kaynak dosyaları Visual Studio XML biçiminden (.resx) bir ara ikili biçime (.resources) derlenmiş ve daha sonra uydu derlemelerine eklenmiş olur. Daha fazla bilgi için [bkz. Visual Studio'da](/dotnet/framework/resources/creating-resource-files-for-desktop-apps#VSResFiles) kaynak dosyaları [ve Masaüstü uygulamaları için uydu derlemeleri oluşturma.](/dotnet/framework/resources/creating-satellite-assemblies-for-desktop-apps)

## <a name="bidirectional-languages"></a>Çift yönlü diller

Metinleri arapça Visual Studio İbranice dahil olmak üzere sağdan sola yazılan dillerde doğru şekilde görüntü alan uygulamalar oluşturmak için Visual Studio'i kullanabilirsiniz. Bazı özellikler için özellikleri kolayca ayarlayabilirsiniz. Diğer durumlarda, kodda özellikleri uygulamalısiniz.

> [!NOTE]
> Çift yönlü dil girmek ve görüntülemek için, uygun dille yapılandırılmış bir Windows sürümüyle çalışıyor olması gerekir. Bu, uygun dil paketinin yüklü olduğu Windows İngilizce bir sürüm veya uygulamanın uygun yerelleştirilmiş Windows.

### <a name="apps-that-support-bidirectional-languages"></a>Çift yönlü dilleri destekleyen uygulamalar

- Windows uygulamaları

   Çift yönlü metin, sağdan sola okuma sırası ve yansıtma (pencerelerin düzenini, menüleri, iletişim kutularını vb.) destekleyen tam çift yönlü uygulamalar oluşturabilirsiniz. Yansıtma dışında, bu özellikler varsayılan olarak veya özellik ayarları olarak kullanılabilir. Yansıtma, ileti kutuları gibi bazı özellikler için doğal olarak de destekler. Ancak, diğer durumlarda kodda yansıtmayı uygulamalısiniz. Daha fazla bilgi için [bkz. Forms uygulamaları için Windows desteği.](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications)

- Web uygulamaları

   Web hizmetleri UTF-8 ve Unicode metinleri göndererek almayı destekler ve bu nedenle çift yönlü diller içeren uygulamalar için uygundur. Web istemcisi uygulamaları kendi kullanıcı arabirimi için tarayıcılara bağımlıdır, bu nedenle bir web uygulamasında çift yönlü destek derecesi, kullanıcının tarayıcısının bu çift yönlü özellikleri ne kadar iyi desteklediğine bağlıdır. Bu Visual Studio Arapça veya İbranice metin, sağdan sola okuma sırası, dosya kodlama ve yerel kültür ayarları desteğine sahip uygulamalar oluşturabilirsiniz. Daha fazla bilgi için [bkz. Web uygulamaları için çift ASP.NET desteği.](/previous-versions/6eedwbtt(v=vs.140))

> [!NOTE]
> Konsol uygulamaları, çift yönlü diller için metin desteğine sahip değildir. Bu, konsol uygulamalarıyla Windows bir sonucudur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de çift yönlü dil desteği](use-bidirectional-languages.md)
- [.NET uygulamalarını genelleştirme ve yerelleştirme](/dotnet/standard/globalization-localization/)
- [.NET uygulamalarındaki kaynaklar](/dotnet/framework/resources/)