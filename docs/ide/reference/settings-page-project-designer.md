---
title: Ayarlar Sayfası, Proje Tasarımcısı
ms.date: 06/14/2018
ms.topic: reference
f1_keywords:
- ApplicationSettingsOverview
helpviewer_keywords:
- Settings page in Project Designer
- Project Designer, Settings page
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f4ca1def334241999445e3f11cf142aa426d962
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566780"
---
# <a name="settings-page-project-designer"></a>Ayarlar sayfası, Proje Tasarımcısı

Projenin uygulama ayarlarını belirtmek için Proje Tasarımcısı'nın **Ayarlar** sayfasını kullanın. Uygulama ayarları, uygulamanız için özellik ayarlarını ve diğer bilgileri dinamik olarak depolamanızı ve almanızı sağlar. Ayrıca, istemci bilgisayarda özel uygulama ve kullanıcı tercihlerini korumanızı da sağlar. Daha fazla bilgi için [bkz.](../managing-application-settings-dotnet.md)

**Ayarlar** sayfasına erişmek için **Çözüm Gezgini'nde**bir proje düğümü seçin ve ardından **Project** > **Properties'i**seçin. Proje Tasarımcısı göründüğünde **Ayarlar** sekmesini seçin.

## <a name="header-bar"></a>Üstbilgi çubuğu

**Ayarlar** sayfasının üst kısmındaki üstbilgi çubuğunda çeşitli denetimler bulunmaktadır:

**Eşitlemek**

**Eşitleme,** uygulamanın çalışma zamanında veya hata ayıklama sırasında tasarım zamanında tanımlandığı gibi varsayılan değerlerine yaptığı kullanıcı kapsamı ayarlarını geri yükler. Verileri geri yüklemek için, proje verilerinden değil, çalışma zamanı oluşturulan uygulamaya özgü dosyaları diskten kaldırın.

**Web Ayarlarını Yükleyin**

**Yük Web Ayarları,** kimlik doğrulaması yapılan bir kullanıcı veya anonim kullanıcılar için ayarları yüklemenizi sağlayan bir **Giriş** iletişim kutusu görüntüler. Bu düğme yalnızca **Hizmetler** sayfasında istemci uygulama hizmetlerini etkinleştirdiğinizde ve **Web ayarları hizmet konumunu**belirttiğinizde etkinleştirilir.

**Kodu Görüntüle**

C# projeleri için **Kodu Görüntüle** *düğmesi, Settings.cs* dosyasındaki kodu görüntülemenizi sağlar. Bu dosya, `Settings` `Settings` nesne üzerinde belirli olayları işlemenize olanak tanıyan sınıfı tanımlar. Visual Basic dışındaki dillerde, kullanıcı ayarlarını sürdürmek için bu sarıcı sınıfının `Save` yöntemini açıkça aramalısınız. Bunu genellikle ana formun **Kapanış** olay işleyicisinde yaparsınız. Aşağıdaki `Save` yönteme bir çağrı örneği:

```csharp
Properties.Settings.Default.Save();
```

Visual Basic projeleri **için, Görünüm Kodu** düğmesi *Ayarlar.vb* dosyasındaki kodu görüntülemenizi sağlar. Bu dosya, `MySettings` `My.Settings` nesne üzerinde belirli olayları işlemenize olanak tanıyan sınıfı tanımlar. Nesneyi kullanarak uygulama ayarlarına erişim `My.Settings` hakkında daha fazla bilgi için [Access uygulama ayarlarına](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)bakın.

Uygulama ayarlarına erişim hakkında daha fazla bilgi [için Windows Formları uygulama ayarlarına](/dotnet/framework/winforms/advanced/application-settings-for-windows-forms)bakın.

**Erişim değiştirici**

**Access değiştirici** düğmesi, Visual Studio'nun `Properties.Settings` `My.Settings` *Settings.Designer.cs* veya *Settings.Designer.vb'de*oluşturduğu (C#) veya (Visual Basic'te) yardımcı sınıflarının erişim düzeyini belirtir.

Visual C# projeleri için erişim değiştirici **Dahili** veya **Genel**olabilir.

Visual Basic projeleri için erişim değiştiricisi **Arkadaş** veya **Ortak**olabilir.

Varsayılan olarak, ayar C#'da **İç ve** Visual Basic'te **Arkadaş'tır.** Visual Studio **Dahili** veya **Arkadaş**olarak yardımcı sınıflar oluşturduğunda , yürütülebilir (*.exe*) uygulamaları sınıf kitaplıklarına *(.dll* dosyaları) eklediğiniz kaynaklara ve ayarlara erişemez. Bir sınıf kitaplığından kaynakları ve ayarları paylaşmanız gerekiyorsa, erişim değiştiriciyi **Genel**olarak ayarlayın.

Ayarlar yardımcı sınıfları hakkında daha fazla bilgi için uygulama [ayarlarını yönet'e](../managing-application-settings-dotnet.md)bakın.

## <a name="settings-grid"></a>Ayarlar ızgarası

**Ayarlar Kılavuz** uygulama ayarlarını yapılandırmak için kullanılır. Bu Kılavuz aşağıdaki sütunları içerir:

**Adı**

Bu alana uygulama ayarı adını girin.

**Tür**

Ayar için bir tür seçmek için açılır listeyi kullanın. En sık kullanılan türler açılır listede görünür, örneğin, **String**, **(Bağlantı dizesi)** ve **System.Drawing.Font**. Listenin sonunda **Gözat'ı** seçerek ve ardından **Tür Seç** iletişim kutusundan bir tür seçerek başka bir tür seçebilirsiniz. Bir tür seçtikten sonra, açılır listedeki ortak türlere eklenir (yalnızca geçerli çözüm için).

**Kapsam**

**Uygulama** veya **Kullanıcı'yı**seçin.

Bağlantı dizeleri gibi uygulama kapsamı ayarları uygulamayla ilişkilidir. Kullanıcılar çalışma zamanında uygulama kapsamı ayarlarını değiştiremez.

Sistem yazı tipleri gibi kullanıcı kapsamı namına ayarların kullanıcı tercihleri için kullanılması amaçlanmıştır. Kullanıcılar bunları çalışma zamanında değiştirebilir.

**Değer**

Uygulama ayarı ile ilişkili veri veya değer. Örneğin, ayar bir yazı tipi ise, değeri **Verdana, 9.75pt, style=Bold**olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama ayarlarını yönetme](../managing-application-settings-dotnet.md)
- [Uygulama ayarlarına erişim (Visual Basic)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
