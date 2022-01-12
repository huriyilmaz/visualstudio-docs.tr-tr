---
title: Xamarin
description: "Mac için Visual Studio 'de Xamarin kullanmak iOS, Mac, Android, tvos ve watchos 'yi hedefleyen platformlar arası uygulamalar oluşturmanıza olanak tanır "
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 06/18/2019
ms.assetid: 339F6051-5F90-48DC-8237-EBBC8A03A32B
ms.topic: how-to
ms.openlocfilehash: 739536f6f632450fec722a38556897bf48baf722
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805305"
---
# <a name="xamarin-mobile-app-development"></a>Xamarin mobil uygulama geliştirme

[Xamarin](/xamarin) için birinci sınıf destekle Android, macOS, iOS, tvOS ve watchOS için zengin yerel deneyimler geliştirebilirsiniz. Xamarin.Forms platformlar arası uygulamaları, yerel işlevselliğe erişimi sınırlamadan Android, iOS ve macOS arasında XAML tabanlı UI kodunu paylaşmanıza yardımcı olur.

## <a name="xamarinforms"></a>Xamarin.Forms

Xamarin. Forms için XAML Hot Reload, sürüm 8,3 ve sonraki sürümlerde Mac için Visual Studio yerleşik olarak bulunur. Bu özellik etkinleştirildiğinde değişiklikler, dosyayı her kaydettiğinizde çalışan uygulamanıza anında yansıtılır.

XAML etkin yeniden yüklemesi, **Visual Studio > tercihleri > projeler > xamarin hot reload**' da, **xamarin hot reload 'i etkinleştir** onay kutusunu işaretleyerek etkinleştirilebilir.

Dinamik yeniden yükleme hakkında daha fazla bilgi için, belgeler içindeki [Xamarin. Forms Için xaml Hot Reload Kılavuzu kılavuzuna](/xamarin/xamarin-forms/xaml/hot-reload) bakın.

## <a name="android"></a>Android

Mac için Visual Studio kendi tümleşik Android SDK yöneticisi 'ne sahiptir ve uygulamanızın hedeflemesini istediğiniz sdk 'lara erişmenizi sağlar.

android uygulamaları için Mac için Visual Studio, kendi tasarımcısını içerir ve bu, `.axml` kullanıcı arabirimlerini görsel olarak oluşturmak için android dosyalarıyla birlikte kullanılır. Mac için Visual Studio, aşağıdaki görüntüde gösterildiği gibi bu dosyaları Android Designer açacak:

![Android kullanıcı arabirimi Tasarımcısı](media/intro-image31.png)

Android Designer hakkında daha fazla bilgi için bkz. [Xamarin. Android Designer genel bakış](/xamarin/android/user-interface/android-designer/index) Kılavuzu.

## <a name="ios"></a>iOS

ios tasarımcısı, Mac için Visual Studio ile tam olarak tümleşiktir ve ios, tvos ve watchos usıs ve geçişleri oluşturmak için. xıb ve görsel taslak dosyalarının görsel düzenlemesini sağlar. Kullanıcı arabiriminin tamamı, araç kutusu ve Tasarım Yüzeyi arasında sürükle ve bırak işlevleri kullanılarak oluşturulabilir, bu da olayları işlemek için sezgisel bir yaklaşım kullanmaktır. İOS Tasarımcısı, tasarım zamanı işlemenin sağladığı avantaja sahip [özel denetimleri](/xamarin/ios/user-interface/designer/ios-designable-controls-overview) de destekler.

![iOS görsel taslak Tasarımcısı](media/intro-image30.png)

İOS tasarımcısını kullanma hakkında daha fazla bilgi için [Tasarımcı](/xamarin/ios/user-interface/designer/?tabs=macos) kılavuzlarını inceleyin.

### <a name="mac"></a>Mac

Xamarin, güzel Mac uygulamaları oluşturmanıza olanak sağlayan yerel Mac API bağlamaları sağlar.

Mac için Visual Studio ile Mac uygulamaları yazma hakkında daha fazla bilgi için [Xamarin. Mac](/xamarin/mac/get-started/index) kılavuzlarını inceleyin.

## <a name="xamarin-enterprise-features"></a>Xamarin Enterprise özellikleri

> [!Note]
> bu ürünler yalnızca Visual Studio Enterprise abonelikle birlikte kullanılabilir.

### <a name="profiler"></a>Profil Oluşturucu

Xamarin Profiler profil oluşturma için kullanılabilen üç araçlar vardır. [Xamarin Profiler kılavuza giriş](/xamarin/tools/profiler/index?tabs=macos) , bu gereçlerin ne ölçmesini ve uygulamanızı nasıl analiz edeceğinizi ve her ekranda sunulan verilerin anlamını açıklığa kavuşturduğunu gösterir.

### <a name="inspector"></a>Denetçi

Xamarin Inspector, Kullanıcı araçlarıyla etkileşimli bir C# konsolu sağlar. Canlı uygulamalar, bir eğitim aracı olarak bir belge aracı veya bir deneme aracı olarak incelenirken hata ayıklama veya tanılama Yardımcısı olarak kullanılabilir.

![Xamarin Inspector](media/intro-inspector.png)

çeşitli programlama platformlarını (Android, iOS, Mac ve Windows) hedefleyebilir ve ıdes hata ayıklama iş akışınıza tümleştirerek, zengin bir C# konsolu sağlayan tek başına bir uygulamadan oluşur.

Daha fazla bilgi için [Xamarin Inspector](/xamarin/tools/inspector/release-notes/1.5) kılavuzuna bakın.
