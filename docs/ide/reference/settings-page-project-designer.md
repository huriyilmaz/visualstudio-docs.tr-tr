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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75566780"
---
# <a name="settings-page-project-designer"></a>Ayarlar sayfası, proje Tasarımcısı

Projenin uygulama ayarlarını belirtmek için proje Tasarımcısı ' nın **Ayarlar** sayfasını kullanın. Uygulama ayarları, uygulamanız için özellik ayarlarını ve diğer bilgileri dinamik olarak depolamanızı ve almanızı sağlar. Ayrıca, bir istemci bilgisayarda özel uygulama ve Kullanıcı tercihlerini korumanıza olanak sağlar. Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme](../managing-application-settings-dotnet.md).

**Ayarlar** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü seçin ve ardından **Proje**  >  **özellikleri**' ni seçin. Proje Tasarımcısı göründüğünde, **Ayarlar** sekmesini seçin.

## <a name="header-bar"></a>Başlık çubuğu

**Ayarlar** sayfasının en üstündeki üst bilgi çubuğu çeşitli denetimler içerir:

**Yapacak**

**Synchronize** , uygulamanın çalışma zamanında veya hata ayıklama sırasında kullandığı kullanıcı kapsamlı ayarları, tasarım zamanında tanımlanan varsayılan değerlerinde geri yükler. Verileri geri yüklemek için, proje verilerinden değil, çalışma zamanı tarafından oluşturulan uygulamaya özgü dosyaları diskten kaldırın.

**Web ayarlarını yükle**

**Web ayarlarını yükle** ayarı, kimliği doğrulanmış bir kullanıcı için veya anonim kullanıcılar için ayarları yüklemeniz sağlayan bir **oturum açma** iletişim kutusu görüntüler. Bu düğme yalnızca, **Hizmetler** sayfasında istemci uygulama hizmetleri 'ni etkinleştirdiğinizde ve bir **Web ayarları hizmet konumu**belirtmişseniz etkindir.

**Kodu Görüntüle**

C# projeleri için, **kodu görüntüle** düğmesi *Settings.cs* dosyasındaki kodu görüntülemenize olanak sağlar. Bu dosya `Settings` , nesnesi üzerinde belirli olayları işleyebilmenizi sağlayan sınıfını tanımlar `Settings` . Visual Basic dışındaki dillerde, `Save` Kullanıcı ayarlarını kalıcı hale getirmek için bu sarmalayıcı sınıfının yöntemini açıkça çağırmanız gerekir. Bunu genellikle ana formun **Kapanış** olay işleyicisinde yapabilirsiniz. Yöntemine yapılan çağrının bir örneği aşağıda verilmiştir `Save` :

```csharp
Properties.Settings.Default.Save();
```

Visual Basic projeleri için, **kodu görüntüle** düğmesi *Settings. vb* dosyasındaki kodu görüntülemenize olanak sağlar. Bu dosya `MySettings` , nesnesi üzerinde belirli olayları işleyebilmenizi sağlayan sınıfını tanımlar `My.Settings` . Nesnesini kullanarak uygulama ayarlarına erişme hakkında daha fazla bilgi için `My.Settings` bkz. [Access Application Settings](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Uygulama ayarlarına erişme hakkında daha fazla bilgi için bkz. [Windows Forms Için uygulama ayarları](/dotnet/framework/winforms/advanced/application-settings-for-windows-forms).

**Erişim değiştiricisi**

**Erişim değiştirici** düğmesi, `Properties.Settings` `My.Settings` Visual Studio 'nun *Settings.Designer.cs* veya *Settings. Designer. vb*içinde oluşturduğu (C# ' de) veya (Visual Basic) yardımcı sınıflarının erişim düzeyini belirtir.

Visual C# projeleri için, erişim değiştiricisi **iç** veya **genel**olabilir.

Visual Basic projeleri için, erişim değiştiricisi **arkadaş** veya **genel**olabilir.

Varsayılan **olarak, ayar** C# ve **arkadaş** Visual Basic. Visual Studio, **iç** veya **arkadaş**olarak yardımcı sınıflar oluşturduğunda, yürütülebilir (*. exe*) uygulamalar, sınıf kitaplıklarına (*. dll* dosyaları) eklediğiniz kaynak ve ayarlara erişemez. Kaynak ve ayarları bir sınıf kitaplığından paylaşmanız gerekiyorsa, erişim değiştiricisini **Public**olarak ayarlayın.

Ayarlar yardımcı sınıfları hakkında daha fazla bilgi için bkz. [uygulama ayarlarını yönetme](../managing-application-settings-dotnet.md).

## <a name="settings-grid"></a>Ayarlar Kılavuzu

**Ayarlar Kılavuzu** , uygulama ayarlarını yapılandırmak için kullanılır. Bu kılavuz şu sütunları içerir:

**Ad**

Uygulama ayarının adını bu alana girin.

**Tür**

Ayar için bir tür seçmek üzere açılır listeyi kullanın. En sık kullanılan türler, örneğin **dize**, **(bağlantı dizesi)** ve **System. Drawing. Font**gibi açılan listede görüntülenir. Listenin sonuna kadar **bul** ' u seçerek ve ardından **bir tür Seç** iletişim kutusunda bir tür seçerek başka bir tür seçebilirsiniz. Bir tür seçtikten sonra, açılan listedeki ortak türlere eklenir (yalnızca geçerli çözüm için).

**Kapsam**

**Uygulama** veya **Kullanıcı**seçin.

Bağlantı dizeleri gibi uygulama kapsamlı ayarlar uygulamayla ilişkilendirilir. Kullanıcılar, çalışma zamanında uygulama kapsamlı ayarları değiştiremezler.

Sistem yazı tipleri gibi kullanıcı kapsamlı ayarların Kullanıcı tercihleri için kullanılması amaçlanmıştır. Kullanıcılar, çalışma zamanında bunları değiştirebilir.

**Değer**

Uygulama ayarıyla ilişkili veri veya değer. Örneğin, ayar bir yazı tipi ise, değeri **Verdana, 9.75 PT, Style = kalın**olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama ayarlarını yönet](../managing-application-settings-dotnet.md)
- [Uygulama ayarlarına erişim (Visual Basic)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
