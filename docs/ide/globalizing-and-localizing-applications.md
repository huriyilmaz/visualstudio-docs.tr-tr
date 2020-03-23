---
title: Yerelleştirme araçları
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9c6934c816574796d59f978c3d2f37f590cf578
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565129"
---
# <a name="develop-globalized-and-localized-apps"></a>Küreselleştirilmiş ve yerelleştirilmiş uygulamalar geliştirme

Visual [Studio, .NET'te](/dotnet/standard/globalization-localization/)yerleşik hizmetlerden yararlanarak uluslararası bir izleyici kitlesi için geliştirmeyi kolaylaştırır.

Örneğin, Windows Forms uygulamaları için proje sistemi, hem geri dönüş ui kültürü hem de her ek Web Sürümü kültürü için kaynak dosyaları oluşturabilir. Visual Studio'da bir proje oluşturduğunuzda, kaynak dosyaları Visual Studio XML biçiminden (.resx) uydu derlemelerine gömülü bir ara ikili biçime (.kaynaklar) derlenir. Daha fazla bilgi için [Visual Studio'daki Kaynak dosyalarına](/dotnet/framework/resources/creating-resource-files-for-desktop-apps#VSResFiles) bakın ve [masaüstü uygulamaları için uydu derlemeleri oluşturun.](/dotnet/framework/resources/creating-satellite-assemblies-for-desktop-apps)

## <a name="bidirectional-languages"></a>Çift yönlü diller

Visual Studio'yu kullanarak Arapça ve İbranice de dahil olmak üzere sağdan sola yazılmış dillerde metni doğru şekilde görüntüleyen uygulamalar oluşturabilirsiniz. Bazı özellikler için yalnızca özellikleri ayarlayabilirsiniz. Diğer durumlarda, kod özellikleri uygulamanız gerekir.

> [!NOTE]
> Çift yönlü dilleri girmek ve görüntülemek için, uygun dille yapılandırılan bir Windows sürümüyle çalışıyor olmalısınız. Bu, uygun dil paketinin yüklü olduğu Windows'un İngilizce sürümü veya Uygun şekilde yerelleştirilmiş Windows sürümü olabilir.

### <a name="apps-that-support-bidirectional-languages"></a>Çift yönlü dilleri destekleyen uygulamalar

- Windows uygulamaları

   Çift yönlü metin, sağdan sola okuma sırası ve yansıtma (pencerelerin, menülerin, iletişim kutularının düzenini tersine çevirme vb.) desteğini içeren tam çift yönlü uygulamalar oluşturabilirsiniz. Yansıtma dışında, bu özellikler varsayılan olarak veya özellik ayarları olarak kullanılabilir. Yansıtma, ileti kutuları gibi bazı özellikler için doğal olarak desteklenir. Ancak, diğer durumlarda kod yansıtma uygulamanız gerekir. Daha fazla bilgi [için Windows Forms uygulamaları için çift yönlü desteğe](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications)bakın.

- Web uygulamaları

   Web hizmetleri UTF-8 ve Unicode metinlerinin gönderilmesini ve alınmasını destekler ve bu da onları çift yönlü diller içeren uygulamalar için uygun hale getirir. Web istemcisi uygulamaları, kullanıcı arabirimi için tarayıcılara güvenir, bu nedenle bir web uygulamasındaki çift yönlü desteğin derecesi, kullanıcının tarayıcısının bu çift yönlü özellikleri ne kadar iyi desteklediğine bağlıdır. Visual Studio'da, Arapça veya İbranice metin, sağdan sola okuma sırası, dosya kodlama ve yerel kültür ayarları desteğiyle uygulamalar oluşturabilirsiniz. Daha fazla bilgi [için, ASP.NET web uygulamaları için Çift Yönlü destek](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03)bakın.

> [!NOTE]
> Konsol uygulamaları çift yönlü diller için metin desteği içermez. Bu, Windows'un konsol uygulamalarıyla çalışma şeklinin bir sonucudur.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da çift yönlü dillere destek](use-bidirectional-languages.md)
- [.NET uygulamalarını küreselleştirin ve yerelleştirin](/dotnet/standard/globalization-localization/)
- [.NET uygulamalarındaki kaynaklar](/dotnet/framework/resources/)
