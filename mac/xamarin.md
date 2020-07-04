---
title: Xamarin
description: "Mac için Visual Studio 'de Xamarin kullanmak iOS, Mac, Android, tvOS ve watchOS 'yi hedefleyen platformlar arası uygulamalar oluşturmanıza olanak tanır "
author: therealjohn
ms.author: johmil
ms.date: 06/18/2019
ms.assetid: 339F6051-5F90-48DC-8237-EBBC8A03A32B
ms.topic: overview
ms.openlocfilehash: e40d9640ca2e62148e4ad166845d8f59854367ff
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950672"
---
# <a name="xamarin-mobile-app-development"></a>Xamarin mobil uygulama geliştirme

[Xamarin](/xamarin) için birinci sınıf destekle Android, macOS, iOS, tvOS ve watchOS için zengin yerel deneyimler geliştirebilirsiniz. Xamarin.Forms platformlar arası uygulamaları, yerel işlevselliğe erişimi sınırlamadan Android, iOS ve macOS arasında XAML tabanlı UI kodunu paylaşmanıza yardımcı olur.

## <a name="xamarinforms"></a>Xamarin.Forms

Xamarin. Forms için XAML Hot reload, sürüm 8,3 ve sonraki sürümlerde Mac için Visual Studio yerleşik olarak bulunur. Bu özellik etkinleştirildiğinde değişiklikler, dosyayı her kaydettiğinizde çalışan uygulamanıza anında yansıtılır.

XAML Hot reload, Visual Studio 'da **Xamarin Hot Reload 'ı etkinleştir** onay kutusunu işaretleyerek etkinleştirilebilir **> tercihleri > projeler > Xamarin Hot Reload**.

Dinamik yeniden yükleme hakkında daha fazla bilgi için, belgeler içindeki [Xamarin. Forms Için xaml Hot Reload Kılavuzu kılavuzuna](/xamarin/xamarin-forms/xaml/hot-reload) bakın.

## <a name="android"></a>Android

Mac için Visual Studio kendi tümleşik Android SDK yöneticisi 'ne sahiptir ve uygulamanızın hedeflemesini istediğiniz SDK 'lara erişmenizi sağlar.

Android uygulamaları için Mac için Visual Studio, kendi tasarımcısını içerir ve bu, `.axml` kullanıcı arabirimlerini görsel olarak oluşturmak Için Android dosyalarıyla birlikte kullanılır. Mac için Visual Studio, aşağıdaki görüntüde gösterildiği gibi bu dosyaları Android Designer açacak:

![Android kullanıcı arabirimi Tasarımcısı](media/intro-image31.png)

Android Designer hakkında daha fazla bilgi için bkz. [Xamarin. Android Designer genel bakış](/xamarin/android/user-interface/android-designer/index) Kılavuzu.

## <a name="ios"></a>iOS

İOS Tasarımcısı, Mac için Visual Studio ile tam olarak tümleşiktir ve iOS, tvOS ve WatchOS Usıs ve geçişleri oluşturmak için. XIB ve görsel taslak dosyalarının görsel düzenlemesini sağlar. Kullanıcı arabiriminin tamamı, araç kutusu ve Tasarım Yüzeyi arasında sürükle ve bırak işlevleri kullanılarak oluşturulabilir, bu da olayları işlemek için sezgisel bir yaklaşım kullanmaktır. İOS Tasarımcısı, tasarım zamanı işlemenin sağladığı avantaja sahip [özel denetimleri](/xamarin/ios/user-interface/designer/ios-designable-controls-overview) de destekler.

![iOS görsel taslak Tasarımcısı](media/intro-image30.png)

İOS tasarımcısını kullanma hakkında daha fazla bilgi için [Tasarımcı](/xamarin/ios/user-interface/designer/?tabs=macos) kılavuzlarını inceleyin.

### <a name="mac"></a>Mac

Xamarin, güzel Mac uygulamaları oluşturmanıza olanak sağlayan yerel Mac API bağlamaları sağlar.

Mac için Visual Studio ile Mac uygulamaları yazma hakkında daha fazla bilgi için [Xamarin. Mac](/xamarin/mac/get-started/index) kılavuzlarını inceleyin.

## <a name="xamarin-enterprise-features"></a>Xamarin kurumsal özellikleri

> [!Note]
> Bu ürünler yalnızca Visual Studio Enterprise abonelikle birlikte kullanılabilir.

### <a name="profiler"></a>Profil Oluşturucu

Xamarin Profiler profil oluşturma için kullanılabilen üç araçlar vardır. [Xamarin Profiler kılavuza giriş](/xamarin/tools/profiler/index?tabs=macos) , bu gereçlerin ne ölçmesini ve uygulamanızı nasıl analiz edeceğinizi ve her ekranda sunulan verilerin anlamını açıklığa kavuşturduğunu gösterir.

### <a name="inspector"></a>Denetçi

Xamarin Inspector, Kullanıcı araçlarıyla etkileşimli bir C# konsolu sağlar. Canlı uygulamalar, bir eğitim aracı olarak bir belge aracı veya bir deneme aracı olarak incelenirken hata ayıklama veya tanılama Yardımcısı olarak kullanılabilir.

![Xamarin Inspector](media/intro-inspector.png)

Çeşitli programlama platformlarını (Android, iOS, Mac ve Windows) hedefleyebilir ve Ides hata ayıklama iş akışınıza tümleştirerek zengin bir C# konsolu sağlayan tek başına bir uygulamadan oluşur.

Daha fazla bilgi için [Xamarin Inspector](/xamarin/tools/inspector/) kılavuzuna bakın.
