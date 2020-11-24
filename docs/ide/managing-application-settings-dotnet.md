---
title: Uygulama ayarlarını yönetme (.NET)
description: Uygulama kodunda bulunmayan, ancak çalışma zamanında gerekli olan uygulama ayarlarını (eskiden dinamik özellikler olarak adlandırılır) yönetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f62e03210e83f434bd32d08c3fe0f7b2b539155e
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596904"
---
# <a name="manage-application-settings-net"></a>Uygulama ayarlarını yönetme (.NET)

Uygulama ayarları, uygulama bilgilerini dinamik olarak depolamanızı sağlar. Ayarları, uygulama kodunda (örneğin bir bağlantı dizesi), kullanıcı tercihlerine ve çalışma zamanında gereken diğer bilgilere dahil edilmemelidir. istemci bilgisayarda bilgi depolamanıza olanak tanır.

Uygulama ayarları, Visual Studio 'nun önceki sürümlerinde kullanılan dinamik özelliklerin yerini alır.

Her uygulama ayarının benzersiz bir adı olmalıdır. Ad, harf, sayı veya sayı ile başlamamayan alt çizginin herhangi bir birleşimi olabilir ve boşluk içeremez. Ad, özelliği aracılığıyla değiştirilir `Name` .

Uygulama ayarları, XML 'e serileştirilmiş veya uygulayan bir veri türü olarak depolanabilir `TypeConverter` `ToString` / `FromString` . En yaygın türler,, `String` `Integer` ve ' dir, `Boolean` ancak değerleri <xref:System.Drawing.Color> , <xref:System.Object> veya bir bağlantı dizesi olarak da depolayabilirler.

Uygulama ayarları da bir değer tutar. Değer, **Value** özelliği ile ayarlanır ve ayarın veri türüyle eşleşmelidir.

Ayrıca, uygulama ayarları, tasarım zamanında bir formun veya denetimin özelliğine bağlanabilir.

Kapsama göre iki tür uygulama ayarı vardır:

- Uygulama kapsamlı ayarlar, bir Web hizmeti URL 'SI veya bir veritabanı bağlantı dizesi gibi bilgiler için kullanılabilir. Bu değerler uygulamayla ilişkilendirilir. Bu nedenle, kullanıcılar çalışma zamanında bunları değiştiremezler.

- Kullanıcı kapsamlı ayarlar, bir formun veya yazı tipi tercihinin son konumunu kalıcı hale getirme gibi bilgiler için kullanılabilir. Kullanıcılar, çalışma zamanında bu değerleri değiştirebilir.

**Kapsam** özelliğini kullanarak bir ayarın türünü değiştirebilirsiniz.

Proje sistemi uygulama ayarlarını iki XML dosyasında depolar:

- ilk uygulama ayarını oluştururken tasarım zamanında oluşturulan bir *app.config* dosyası

- uygulamayı çalıştıran kullanıcı herhangi bir kullanıcı ayarının değerini değiştirdiğinde çalışma zamanında oluşturulan bir *user.config* dosyası.

Uygulama özellikle bunu yapmak için bir yöntem çağırmadığı takdirde Kullanıcı ayarlarındaki değişikliklerin diske yazılmadığından emin olun.

## <a name="create-application-settings-at-design-time"></a>Tasarım zamanında uygulama ayarları oluşturma

Tasarım zamanında, uygulama ayarlarını iki şekilde oluşturabilirsiniz: **Proje Tasarımcısı**'nın **Ayarlar** sayfasını veya bir form veya denetim için **Özellikler** penceresini kullanarak bir özelliği bir özelliğe bağlamanıza olanak tanır.

Uygulama kapsamlı bir ayar oluşturduğunuzda (örneğin, bir veritabanı bağlantı dizesi veya sunucu kaynaklarına bir başvuru), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] etiketi ile *app.config* kaydeder `<applicationSettings>` . (Bağlantı dizeleri etiketinin altına kaydedilir `<connectionStrings>` .)

Kullanıcı kapsamlı bir ayar oluşturduğunuzda (örneğin, varsayılan yazı tipi, giriş sayfası veya pencere boyutu), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] etiketi ile *app.config* kaydeder `<userSettings>` .

> [!IMPORTANT]
> Bağlantı dizelerini *app.config* depoladığınızda, bağlantı dizesinde parolalar veya sunucu yolları gibi hassas bilgilerin görüntülenmesinden kaçınmak için önlemler almalısınız.
>
> Bir dış kaynaktan bir kullanıcı KIMLIĞI ve parola sağlayan bağlantı dizesi bilgileri alırsanız, Bağlantı dizenizi oluşturmak için kullandığınız değerlerin bağlantınızın davranışını değiştiren ek bağlantı dizesi parametreleri içermediğinden emin olmak için dikkatli olmanız gerekir.
>
> Yapılandırma dosyasındaki hassas bilgileri şifrelemek için korumalı yapılandırma özelliğini kullanmayı düşünün. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](/dotnet/framework/data/adonet/protecting-connection-information).

> [!NOTE]
> Sınıf kitaplıkları için yapılandırma dosyası modeli olmadığından, sınıf kitaplığı projeleri için uygulama ayarları uygulanmaz. Özel durum, bir yapılandırma dosyası olabilen Office DLL projesi için bir Visual Studio Araçları.

## <a name="use-customized-settings-files"></a>Özelleştirilmiş ayarlar dosyalarını kullan

Ayar gruplarının kolay yönetimi için projenize özelleştirilmiş ayarlar dosyaları ekleyebilirsiniz. Tek bir dosyada bulunan ayarlar bir birim olarak yüklenir ve kaydedilir. Ayarları, sık kullanılan ve seyrek kullanılan gruplar için ayrı dosyalarda depolamak, ayarları yükleme ve kaydetme sırasında zamandan tasarruf edebilir.

Örneğin, projenize *SpecialSettings. Settings* gibi bir dosya ekleyebilirsiniz. `SpecialSettings`Sınıfınız `My` ad alanında gösterilmediğinden, **Görünüm kodu** içeren özel ayarlar dosyasını okuyabilir `Partial Class SpecialSettings` .

**Ayarlar Tasarımcısı** öncelikle proje sisteminin oluşturduğu *Settings. Settings* dosyasını arar; Bu dosya, **Proje tasarımcısının** **Ayarlar** sekmesinde görüntülediği varsayılan dosyadır. *Settings. Settings* , projeler için *My projem* klasöründe [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ve projeler için *Özellikler* klasöründe bulunur [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] . **Proje Tasarımcısı** daha sonra projenin kök klasöründeki diğer ayarlar dosyalarını arar. Bu nedenle, özel ayarlar dosyanızı buraya koymanız gerekir. Projeniz başka bir yerde bir *. Settings* dosyası eklerseniz, **Proje Tasarımcısı** bunu bulamaz.

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Visual Basic çalışma zamanında uygulama ayarlarını erişim veya değiştirme

Visual Basic projelerinde, nesnesini kullanarak çalışma zamanında uygulama ayarlarına erişebilirsiniz `My.Settings` . **Ayarlar sayfasında,** *Settings. vb* dosyasını görüntülemek için **kodu görüntüle** düğmesine tıklayın. *Settings. vb* , `Settings` Ayarlar sınıfında bu olayları idare etmenizi sağlayan sınıfını tanımlar: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> ,, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged> <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded> ve <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> . `Settings` *Settings. vb* dosyasındaki sınıfın, tüm oluşturulan sınıfı değil yalnızca kullanıcıya ait kodu görüntüleyen kısmi bir sınıf olduğunu unutmayın. Nesnesini kullanarak uygulama ayarlarına erişme hakkında daha fazla bilgi için `My.Settings` bkz. [erişim uygulama ayarları (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Kullanıcının çalışma zamanında değiştiği kullanıcı kapsamlı ayarların değerleri (örneğin, bir formun konumu) *user.config* bir dosyada depolanır. Varsayılan değerlerin *app.config* hala kaydedildiğinden emin olun.

Çalışma zamanında Kullanıcı tanımlı herhangi bir ayar değiştirilmişse, örneğin, uygulamayı test etmek ve bu ayarları varsayılan değerlerine sıfırlamak istiyorsanız, **Synchronize** düğmesine tıklayın.

`My.Settings`Ayarlara erişmek için nesneyi ve Default *. Settings* dosyasını kullanmanızı önemle tavsiye ederiz. Bunun nedeni, ayarlara Özellikler atamak için **Ayarlar tasarımcısını** kullanabilir ve ek olarak, Uygulama kapanmadan önce Kullanıcı ayarları otomatik olarak kaydedilir. Ancak, Visual Basic uygulamanız ayarlara doğrudan erişebilir. Bu durumda, `MySettings` sınıfa erişmeniz ve projenin kökünde özel bir *. Settings* dosyası kullanmanız gerekir. Bir C# uygulaması için yaptığınız gibi, uygulamayı sonlandırmadan önce Kullanıcı ayarlarını kaydetmeniz gerekir; Bu, aşağıdaki bölümde açıklanmıştır.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="access-or-change-application-settings-at-run-time-in-c"></a>C 'de çalışma zamanında uygulama ayarlarına erişme veya uygulama ayarlarını değiştirme #
<!-- markdownlint-enable MD003 MD020 -->

C# gibi Visual Basic dışındaki dillerde, `Settings` Aşağıdaki örnekte gösterildiği gibi, sınıfa doğrudan erişmeniz gerekir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

`Save`Kullanıcı ayarlarını kalıcı hale getirmek için bu sarmalayıcı sınıfının yöntemini açıkça çağırmanız gerekir. Bunu genellikle `Closing` ana formun olay işleyicisinde yapabilirsiniz. Aşağıdaki C# örneği yöntemine bir çağrı gösterir `Save` .

```csharp
Properties.Settings.Default.Save();
```

Uygulama ayarlarına sınıfı aracılığıyla erişme hakkında genel bilgi için `Settings` bkz. [uygulama ayarlarına genel bakış (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview). Ayarlar arasında yineleme yapma hakkında daha fazla bilgi için bu [Forum gönderisini](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral)inceleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama ayarlarına erişim (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
