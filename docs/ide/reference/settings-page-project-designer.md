---
title: Ayarlar Sayfası, Proje Tasarımcısı
description: Projenin uygulama ayarlarını Ayarlar için Project Tasarımcısı'nın Project sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/14/2018
ms.topic: reference
f1_keywords:
- ApplicationSettingsOverview
helpviewer_keywords:
- Settings page in Project Designer
- Project Designer, Settings page
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 5d65fcf4097069c48061f45d26293178cab2f379
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150995"
---
# <a name="settings-page-project-designer"></a>Ayarlar sayfası, Project Tasarımcısı

Projenin **Ayarlar** ayarlarını belirtmek için Project Tasarımcısı'nın Project sayfasını kullanın. Uygulama ayarları, uygulamanıza ilişkin özellik ayarlarını ve diğer bilgileri dinamik olarak depolamanızı ve alamanızı sağlar. Ayrıca istemci bilgisayarda özel uygulama ve kullanıcı tercihlerini korumanızı sağlar. Daha fazla bilgi için [bkz. Uygulama ayarlarını yönetme.](../managing-application-settings-dotnet.md)

Giriş sayfasına **Ayarlar** için, Çözüm Gezgini'de bir **proje düğümü seçin** ve ardından Özellikler'Project   >  **seçin.** Project Tasarımcısı görüntülendiğinde, **Ayarlar** sekmesini seçin.

## <a name="header-bar"></a>Başlık çubuğu

Ayarlar sayfasının üst **Ayarlar** denetimler vardır:

**Eşitlemek**

**Eşitleme,** uygulamanın çalışma zamanında veya hata ayıklama sırasında kullandığı kullanıcı kapsamlı ayarları tasarım zamanında tanımlandığı şekilde varsayılan değerlerine geri yükleyebilir. Verileri geri yüklemek için proje verilerinden değil, diskten çalışma zamanında oluşturulan uygulamaya özgü dosyaları kaldırın.

**Web uygulaması Ayarlar**

**Web Sitesini Ayarlar,** kimliği **doğrulanmış** bir kullanıcı veya anonim kullanıcılar için ayarları yüklemene olanak sağlayan bir Oturum Açma iletişim kutusu görüntüler. Bu düğme yalnızca Hizmetler sayfasında istemci uygulama hizmetlerini etkinleştirdiyseniz ve bir Web **ayarları** hizmet konumu **belirttiğinizde etkinleştirilir.**

**Kodu Görüntüle**

C# projeleri için Kodu **Görüntüle** düğmesi, kodu *Ayarlar.cs dosyasında görüntülemeyi* sağlar. Bu dosya, `Settings` nesnede belirli olayları işlemeye olanak sağlayan sınıfını `Settings` tanımlar. Kullanıcı ayarlarını kalıcı Visual Basic için bu sarmalayıcı sınıfının yöntemini açıkça çağırmalı ve diğer dillerde `Save` çağırabilirsiniz. Bunu genellikle ana formun **Kapanış** olayı işleyicisinde yaparsiniz. Aşağıda, yöntemine yapılan çağrının bir örneği `Save` ve bir örneği vetir:

```csharp
Properties.Settings.Default.Save();
```

Daha Visual Basic için Kodu **Görüntüle** düğmesi, *kodu Ayarlar.vb* dosyasında görüntülemeyi sağlar. Bu dosya, `MySettings` nesnede belirli olayları işlemeye olanak sağlayan sınıfını `My.Settings` tanımlar. nesnesini kullanarak uygulama ayarlarına erişme hakkında daha fazla bilgi `My.Settings` için [bkz. Uygulama ayarlarına erişme.](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)

Uygulama ayarlarına erişme hakkında daha fazla bilgi için [bkz. Windows Forms için uygulama ayarları.](/dotnet/framework/winforms/advanced/application-settings-for-windows-forms)

**Erişim değiştiricisi**

Erişim **değiştirici düğmesi,** Visual Studio tarafından oluşturulan yardımcı sınıfların `Properties.Settings` (C# içinde) veya `My.Settings` (Visual Basic) erişim *Ayarlar. Designer.cs* veya *Ayarlar. Designer.vb*.

Visual C# projeleri için erişim değiştiricisi İç veya **Genel** **olabilir.**

Daha Visual Basic için erişim değiştiricisi Arkadaş veya **Genel** **olabilir.**

Varsayılan olarak, ayar C# **içinde Dahili** ve şirket içi **arkadaş** Visual Basic. Bu Visual Studio İç veya Arkadaş **,** yürütülebilir (*.exe*) olarak yardımcı sınıflar oluşturması, sınıf kitaplıklarına *ekley* istediğiniz kaynaklara ve ayarlara (.dlldosyaları) erişemektedir.  Bir sınıf kitaplığından kaynakları ve ayarları paylaşmanız gerekirse, erişim değiştiricisini Genel olarak **ayarlayın.**

Ayarlar yardımcı sınıfları hakkında daha fazla bilgi için bkz. [Uygulama ayarlarını yönetme.](../managing-application-settings-dotnet.md)

## <a name="settings-grid"></a>Ayarlar kılavuzu

**Ayarlar Grid,** uygulama ayarlarını yapılandırmak için kullanılır. Bu kılavuz aşağıdaki sütunları içerir:

**Ad**

Bu alana uygulama ayarının adını girin.

**Tür**

Ayar için bir tür seçmek üzere açılan listeyi kullanın. En sık kullanılan türler açılan listede görünür; örneğin, **Dize**, **(Bağlantı dizesi)** ve **System.Drawing.Font**. Listenin sonunda gözat'ı **ve** ardından Tür Seçin iletişim kutusundan bir tür seçerek **başka bir tür** seçebilirsiniz. Bir tür seçtikten sonra, açılır listede ortak türlere eklenir (yalnızca geçerli çözüm için).

**Kapsam**

Uygulama veya **Kullanıcı'ya** **tıklayın.**

Bağlantı dizeleri gibi uygulama kapsamlı ayarlar uygulamayla ilişkilendirilmektedir. Kullanıcılar çalışma zamanında uygulama kapsamlı ayarları değiştiremez.

Sistem yazı tipleri gibi kullanıcı kapsamlı ayarlar, kullanıcı tercihleri için kullanılmak üzere tasarlanmıştır. Kullanıcılar çalışma zamanında bunları değiştirebilir.

**Değer**

Uygulama ayarıyla ilişkili veriler veya değer. Örneğin, ayar bir yazı tipi ise değeri **Verdana, 9,75pt, style=Bold olabilir.**

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama ayarlarını yönetme](../managing-application-settings-dotnet.md)
- [Uygulama ayarlarına erişme (Visual Basic)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
