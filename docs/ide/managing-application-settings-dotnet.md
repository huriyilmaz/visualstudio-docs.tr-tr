---
title: Uygulama ayarlarını yönetme (.NET)
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
ms.openlocfilehash: 8d792a6147795f81211203fc442539371f3caa91
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593713"
---
# <a name="manage-application-settings-net"></a>Uygulama ayarlarını yönetme (.NET)

Uygulama ayarları, uygulama bilgilerini dinamik olarak depolamanızı sağlar. Ayarlar, istemci bilgisayarda uygulama koduna (örneğin bağlantı dizesi), kullanıcı tercihleri ve çalışma sırasında gereksinim duyduğunuz diğer bilgileri dahil edilmemesi gereken bilgileri depolamanıza olanak tanır.

Uygulama ayarları Visual Studio'nun önceki sürümlerinde kullanılan dinamik özelliklerin yerini alır.

Her uygulama ayarı benzersiz bir ada sahip olmalıdır. Ad, harf, sayı veya bir sayıyla başlamayan bir alt alt anlama birleşimi olabilir ve boşlukları olamaz. Ad `Name` özellik aracılığıyla değiştirilir.

Uygulama ayarları XML'e serileştirilmiş veya bir 'yi uygulayan `TypeConverter` `ToString` / `FromString`herhangi bir veri türü olarak depolanabilir. En yaygın türleri `String` `Integer`, `Boolean`, ve , ama <xref:System.Drawing.Color>aynı <xref:System.Object>zamanda , , olarak veya bir bağlantı dize olarak değerleri depolayabilirsiniz.

Uygulama ayarları da bir değer tutar. Değer **değeri** özelliğiyle ayarlanır ve ayarın veri türüyle eşleşmesi gerekir.

Buna ek olarak, uygulama ayarları tasarım zamanında bir form veya denetim özelliğine bağlanabilir.

Kapsama göre iki tür uygulama ayarı vardır:

- Uygulama kapsamı ayarları, bir web hizmetinin URL'si veya veritabanı bağlantı dizesi gibi bilgiler için kullanılabilir. Bu değerler uygulama ile ilişkilidir. Bu nedenle, kullanıcılar bunları çalışma zamanında değiştiremez.

- Kullanıcı kapsamı ayarları, formun son konumunu veya yazı tipi tercihini sürdürmek gibi bilgiler için kullanılabilir. Kullanıcılar bu değerleri çalışma zamanında değiştirebilir.

**Kapsam** özelliğini kullanarak ayar türünü değiştirebilirsiniz.

Proje sistemi uygulama ayarlarını iki XML dosyasında depolar:

- ilk uygulama ayarını oluşturduğunuzda tasarım zamanında oluşturulan bir *app.config* dosyası

- uygulamayı çalıştıran kullanıcı herhangi bir kullanıcı ayarını değiştirdiğinde çalışma zamanında oluşturulan *user.config* dosyası.

Uygulama özellikle bunu yapmak için bir yöntem çağırmadığı sürece kullanıcı ayarlarındaki değişikliklerin diske yazılmadığını unutmayın.

## <a name="create-application-settings-at-design-time"></a>Tasarım zamanında uygulama ayarları oluşturma

Tasarım zamanında, uygulama ayarlarını iki şekilde oluşturabilirsiniz: Proje **Tasarımcısı'nın** **Ayarlar** sayfasını kullanarak veya bir ayarı bir özelliğe bağlamanızı sağlayan bir form veya denetim için **Özellikler** penceresini kullanarak.

Uygulama kapsamında bir ayar (örneğin, bir veritabanı bağlantı dizesi veya sunucu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kaynaklarına bir başvuru) oluşturduğunuzda, bu ayarı `<applicationSettings>` etiketle birlikte *app.config'e* kaydeder. (Bağlantı dizeleri etiketin `<connectionStrings>` altına kaydedilir.)

Kullanıcı kapsamında bir ayar oluşturduğunuzda (örneğin, varsayılan yazı tipi, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] giriş sayfası veya pencere boyutu), `<userSettings>` etiketiyle birlikte *app.config'e* kaydeder.

> [!IMPORTANT]
> Bağlantı dizelerini *app.config'de*depolarken, bağlantı dizesinde parolalar veya sunucu yolları gibi hassas bilgilerin açığa çıkmasından kaçınmak için önlemler almalısınız.
>
> Bağlantı dize bilgilerini, kullanıcı kimliği ve parola sağlayan bir kullanıcı gibi harici bir kaynaktan alırsanız, bağlantı dizenizi oluşturmak için kullandığınız değerlerin ek bağlantı dize parametreleri içermediğinden emin olmak için dikkatli olmalısınız bağlantınızın davranışını değiştirir.
>
> Yapılandırma dosyasındaki hassas bilgileri şifrelemek için Korumalı Yapılandırma özelliğini kullanmayı düşünün. Daha fazla bilgi için [bkz.](/dotnet/framework/data/adonet/protecting-connection-information)

> [!NOTE]
> Sınıf kitaplıkları için yapılandırma dosyası modeli olmadığından, Sınıf Kitaplığı projeleri için uygulama ayarları geçerli değildir. Bunun istisnası, yapılandırma dosyası na sahip olabilecek Office DLL projesi için Görsel Stüdyo Araçlarıdır.

## <a name="use-customized-settings-files"></a>Özelleştirilmiş ayarlar dosyalarını kullanma

Ayar gruplarının uygun yönetimi için projenize özelleştirilmiş ayarlar dosyaları ekleyebilirsiniz. Tek bir dosyada bulunan ayarlar yüklenir ve birim olarak kaydedilir. Sık kullanılan ve seyrek kullanılan gruplar için ayarları ayrı dosyalarda depolamak yükleme ve kaydetme ayarlarında zamandan tasarruf sağlayabilir.

Örneğin, projenize *SpecialSettings.settings* gibi bir dosya ekleyebilirsiniz. Sınıfınız `SpecialSettings` `My` ad alanında açıkta olmasa **da, Görünüm Kodu** ' `Partial Class SpecialSettings`yu içeren özel ayarlar dosyasını okuyabilir.

**Ayarlar Tasarımcısı** ilk olarak proje sisteminin oluşturduğu *Ayarlar ayarlar* dosyasını arar; Bu dosya, **Project Designer'ın** **Ayarlar** sekmesinde görüntülenebilen varsayılan dosyadır. Ayarlar *Ayarlar* projeler için [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *Projem* klasöründe ve projeler için [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] *Özellikler* klasöründe bulunur. **Proje Tasarımcısı** daha sonra projenin kök klasöründeki diğer ayarlar dosyalarını arar. Bu nedenle, özel ayarlar dosyanızı oraya koymalısınız. Projenizin başka bir yerinde bir *.settings* dosyası eklerseniz, **Proje Tasarımcısı** dosyayı budosyayı bulamaz.

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Visual Basic'te çalışma saatinde uygulama ayarlarına erişin veya değiştirin

Visual Basic projelerinde, nesneyi kullanarak çalışma zamanında `My.Settings` uygulama ayarlarına erişebilirsiniz. **Ayarlar** sayfasında, *Ayarlar.vb* dosyasını görüntülemek için **Kodu Görüntüle** düğmesini tıklatın. *Settings.vb,* ayarlar `Settings` sınıfında bu olayları işlemenizi sağlayan sınıfı <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>tanımlar: <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged> <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>, <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, ve . `Settings` *Settings.vb'deki* sınıfın, oluşturulan sınıfın tamamını değil, yalnızca kullanıcıya ait kodu görüntüleyen kısmi bir sınıf olduğuna dikkat edin. Nesneyi kullanarak uygulama ayarlarına `My.Settings` erişim hakkında daha fazla bilgi için Access uygulama [ayarlarına (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)bakın.

Kullanıcının çalışma zamanında değiştirdiği kullanıcı kapsamı ayarlarının değerleri (örneğin, formun konumu) *user.config* dosyasında depolanır. Varsayılan değerlerin *hala app.config'de*kayda değer olduğuna dikkat edin.

Çalışma süresi sırasında kullanıcı kapsamı içinde olan ayarlar (örneğin uygulama nın sınanması sırasında) değiştirilirse ve bu ayarları varsayılan değerlerine sıfırlamak isterse, **Eşitle** düğmesini tıklatın.

Ayarlara erişmek için nesneyi `My.Settings` ve varsayılan *.settings* dosyasını kullanmanızı şiddetle öneririz. Bunun nedeni, ayarlara özellikler atamak için **Ayarlar Tasarımcısı'nı** kullanabilmek ve ayrıca uygulama kapanmadan önce kullanıcı ayarlarının otomatik olarak kaydolmasıdır. Ancak Visual Basic uygulamanız ayarlara doğrudan erişebilir. Bu durumda `MySettings` sınıfa erişmeniz ve projenin kökünde özel bir *.settings* dosyası kullanmanız gerekir. C# uygulaması için yaptığınız gibi uygulamayı sonlandırdıktan önce kullanıcı ayarlarını kaydetmeniz gerekir; bu aşağıdaki bölümde açıklanmıştır.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="access-or-change-application-settings-at-run-time-in-c"></a>C'de çalışma saatinde uygulama ayarlarına erişin veya değiştirin #
<!-- markdownlint-enable MD003 MD020 -->

C# gibi Visual Basic dışındaki dillerde, aşağıdaki `Settings` [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] örnekte gösterildiği gibi sınıfa doğrudan erişmelisiniz.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Kullanıcı ayarlarını sürdürmek `Save` için bu sarıcı sınıfının yöntemini açıkça aramalısınız. Bunu genellikle ana `Closing` formun olay işleyicisi olarak yaparsınız. Aşağıdaki C# örneği `Save` yönteme bir çağrı gösterir.

```csharp
Properties.Settings.Default.Save();
```

Sınıf üzerinden uygulama ayarlarına `Settings` erişim hakkında genel bilgi için Uygulama [ayarlarına genel bakış (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview)bakın. Ayarlar aracılığıyla yinelenme hakkında bilgi için bu [forum gönderisi](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama ayarlarına erişim (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
