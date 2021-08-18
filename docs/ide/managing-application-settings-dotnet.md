---
title: Uygulama ayarlarını yönetme (.NET)
description: Uygulama koduna dahil edilen ancak çalışma zamanında gerekli olan uygulama ayarlarını (eski adı dinamik özellikler) yönetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 608870ed029eb15b205ae10da4c21daba04a8dea
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069476"
---
# <a name="manage-application-settings-net"></a>Uygulama ayarlarını yönetme (.NET)

Uygulama ayarları, uygulama bilgilerini dinamik olarak depolamaya olanak sağlar. Ayarlar uygulama koduna (örneğin bir bağlantı dizesi), kullanıcı tercihleri ve çalışma zamanında ihtiyacınız olan diğer bilgilere dahil edilecek bilgileri istemci bilgisayarda depolamanızı sağlar.

Uygulama ayarları, uygulama ayarlarının önceki sürümlerinde kullanılan dinamik Visual Studio.

Her uygulama ayarının benzersiz bir adı olmalıdır. Ad harf, sayı veya alt çizgi birleşimi olabilir ve sayı ile başlamaz ve boşluk olamaz. Ad özelliği aracılığıyla `Name` değiştirilir.

Uygulama ayarları, XML'ye seri hale getirilen veya uygulayan bir veri `TypeConverter` türü olarak depolanmış `ToString` / `FromString` olabilir. En yaygın türler , ve türleridir, ancak değerleri bir bağlantı dizesi `String` olarak , veya olarak da `Integer` `Boolean` <xref:System.Drawing.Color> <xref:System.Object> depolarsınız.

Uygulama ayarları da bir değer tutar. Değer, Value **özelliğiyle ayarlanır** ve ayarın veri türüyle eşleşmesi gerekir.

Ayrıca, uygulama ayarları tasarım zamanında bir formun veya denetimin özelliğine bağlı olabilir.

Kapsamı temel alan iki tür uygulama ayarı vardır:

- Uygulama kapsamlı ayarlar, bir web hizmetinin URL'si veya veritabanı bağlantı dizesi gibi bilgiler için kullanılabilir. Bu değerler uygulamayla ilişkilendirildi. Bu nedenle, kullanıcılar çalışma zamanında bunları değiştiremez.

- Kullanıcı kapsamlı ayarlar, formun son konumunun kalıcı olması veya yazı tipi tercihi gibi bilgiler için kullanılabilir. Kullanıcılar bu değerleri çalışma zamanında değiştirebilir.

Kapsam özelliğini kullanarak bir ayarın türünü **değiştirebilirsiniz.**

Proje sistemi uygulama ayarlarını iki XML dosyasında depolar:

- bir *app.config* dosyası, ilk uygulama ayarını oluşturulduğunda tasarım zamanında oluşturulur

- bir *user.config* dosyası, uygulamayı çalıştıran kullanıcı herhangi bir kullanıcı ayarının değerini değiştirirken çalışma zamanında oluşturulur.

Uygulama bunu yapmak için özellikle bir yöntem çağırmadıkça kullanıcı ayarlarında yapılan değişikliklerin diske yazıldığına dikkat edin.

## <a name="create-application-settings-at-design-time"></a>Tasarım zamanında uygulama ayarları oluşturma

Tasarım zamanında, uygulama ayarlarını iki şekilde oluşturabilirsiniz: **Project Tasarımcısı'nın** **Ayarlar** sayfasını kullanarak veya  bir form veya denetim için Özellikler penceresini kullanarak bir ayarı bir özelle bağlamanızı sağlar.

Uygulama kapsamlı bir ayar (örneğin, veritabanı bağlantı dizesi veya sunucu kaynaklarına başvuru) oluşturursanız, bunuapp.config[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] etiketiyle  `<applicationSettings>` kaydeder. (Bağlantı dizeleri etiketi altına `<connectionStrings>` kaydedilir.)

Kullanıcı kapsamlı bir ayar sanız (örneğin, varsayılan yazı tipi, giriş sayfası veya pencere boyutu), bunu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] *etiketliapp.config* olarak `<userSettings>` kaydeder.

> [!IMPORTANT]
> bağlantı dizelerini *app.config,* bağlantı dizesinde parolalar veya sunucu yolları gibi hassas bilgilerin açığa çıkarılmasından kaçınmak için önlemler alasınız.
>
> Bir dış kaynaktan kullanıcı kimliği ve parola alan bir kullanıcı gibi bağlantı dizesi bilgilerini alırsanız, bağlantı dizenizi oluşturmak için kullanabileceğiniz değerlerin bağlantı davranışını değiştirecek ek bağlantı dizesi parametreleri içermeyebilirsiniz.
>
> Yapılandırma dosyasındaki hassas bilgileri şifrelemek için Korumalı Yapılandırma özelliğini kullanmayı göz önünde bulundurabilirsiniz. Daha fazla bilgi için [bkz. Bağlantı bilgilerini koruma.](/dotnet/framework/data/adonet/protecting-connection-information)

> [!NOTE]
> Sınıf kitaplıkları için yapılandırma dosya modeli olduğundan, uygulama ayarları Sınıf Kitaplığı projeleri için geçerli değildir. Özel durum, Office için Visual Studio Araçları dosyası buluna bir DLL projesidir.

## <a name="use-customized-settings-files"></a>Özelleştirilmiş ayarlar dosyalarını kullanma

Ayar gruplarının kolay yönetimi için projenize özelleştirilmiş ayarlar dosyaları eklemek için bunu yapabilirsiniz. Ayarlar dosyada yer alan tüm bilgiler yüklenir ve birim olarak kaydedilir. Sık kullanılan ve seyrek kullanılan gruplar için ayarları ayrı dosyalarda depolamak, ayarları yükleme ve kaydetmeye zaman tasarrufu sağlar.

Örneğin, projenize *SpecialSettings.settings gibi bir dosya* eklersiniz. Sınıfınız `SpecialSettings` ad alanı içinde açığa `My` çıkarılamasa da, **Kodu** Görüntüle, içeren özel ayarlar dosyasını `Partial Class SpecialSettings` okuyabilir.

Ayarlar **Tasarımcısı ilk** olarak proje sisteminin oluşturduğu *Ayarlar.settings* dosyasını arar; Bu **dosya, Project Designer'ın** **Ayarlar** sekmesinde görüntülene varsayılan dosyadır. *Ayarlar.settings,* projeler için *My Project* klasöründe ve projeler için [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] *Özellikler* klasöründe [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] bulunur. Ardından **Project Tasarımcısı,** projenin kök klasöründeki diğer ayarlar dosyalarını arar. Bu nedenle, özel ayarlar dosyanızı buraya koyabilirsiniz. Projenizin başka *bir yerinde bir .settings* dosyası ekler Project Tasarımcı dosyayı bulamaz. 

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Çalışma zamanında uygulama ayarlarına erişim veya Visual Basic

Bu Visual Basic, çalışma zamanında nesne kullanarak uygulama ayarlarına `My.Settings` erişebilirsiniz. Ayarlar.vb dosyasını **görüntülemek** için Kodu görüntüle düğmesine *Ayarlar* tıklayın.  *Ayarlar.vb,* bu olayları ayarlar sınıfında işlemeye olanak sağlayan `Settings` sınıfını tanımlar: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> , , ve <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged> <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded> <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> . Ayarlar.vb'de sınıfının, oluşturulan sınıfın tamamını değil yalnızca kullanıcıya ait kodu görüntüleyen `Settings` kısmi bir sınıf olduğunu fark vardır.  nesnesini kullanarak uygulama ayarlarına erişme hakkında daha fazla bilgi `My.Settings` için [bkz. Uygulama ayarlarına erişme (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Kullanıcının çalışma zamanında değiştir olduğu tüm kullanıcı kapsamlı ayarların değerleri (örneğin, formun konumu) biruser.config *depolanır.* Varsayılan değerlerin yine de *app.config.*

Çalışma zamanında, örneğin uygulamayı test etme sırasında kullanıcı kapsamlı ayarlar değiştirilirse ve bu ayarları varsayılan değerlerine sıfırlamak için Eşitle **düğmesine** tıklayın.

Ayarlara erişmek için nesnesini `My.Settings` ve varsayılan *.settings dosyasını* kullanmanız önemle önerilir. Bunun nedeni, Ayarlar **Designer'ın** ayarlara özellik atamak için kullana biliyor ve buna ek olarak, kullanıcı ayarlarının uygulama kapanmadan önce otomatik olarak kaydedilebilir. Ancak, Visual Basic doğrudan ayarlara erişebilirsiniz. Bu durumda sınıfına erişmeniz `MySettings` ve projenin kökünde *özel bir .settings* dosyası kullansanız gerekir. Bir C# uygulaması için olduğu gibi uygulamayı sonlandırmadan önce kullanıcı ayarlarını kaydetmeniz gerekir; Bu, aşağıdaki bölümde açıklanmıştır.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="access-or-change-application-settings-at-run-time-in-c"></a>C'de çalışma zamanında uygulama ayarlarına erişme veya ayarları değiştirme #
<!-- markdownlint-enable MD003 MD020 -->

C# gibi Visual Basic dillerde, aşağıdaki örnekte gösterildiği gibi `Settings` sınıfına doğrudan [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] erişmelisiniz.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Kullanıcı ayarlarını kalıcı yapmak `Save` için bu sarmalayıcı sınıfının yöntemini açıkça çağırmalısiniz. Bunu genellikle ana formun `Closing` olay işleyicisinde yaparsiniz. Aşağıdaki C# örneği, yöntemine yapılan bir çağrıyı `Save` gösterir.

```csharp
Properties.Settings.Default.Save();
```

sınıf aracılığıyla uygulama ayarlarına erişme hakkında genel bilgi için bkz. Uygulama `Settings` [ayarlarına genel bakış (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview). Ayarlar aracılığıyla tekrarla hakkında daha fazla bilgi için bu [forum gönderisi'ne bakın.](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral)

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama ayarlarına erişme (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
