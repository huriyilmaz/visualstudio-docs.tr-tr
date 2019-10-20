---
title: Uygulama ayarlarını yönetme (.NET) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
ms.assetid: 35254321-ad14-47d9-b8c6-39ab3203c5d9
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b37ed78f9b67d10c0bf845a5bd7340f1f38557bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651421"
---
# <a name="managing-application-settings-net"></a>Uygulama Ayarlarını Yönetme

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulama ayarları, uygulama bilgilerini dinamik olarak depolamanızı sağlar. Ayarları, istemci bilgisayarda uygulama koduna (örneğin bir bağlantı dizesi), kullanıcı tercihlerine ve çalışma zamanında ihtiyacınız olan diğer bilgilere dahil olmaması gereken bilgileri depolamanıza olanak tanır.

Uygulama ayarları, Visual Studio 'nun önceki sürümlerinde kullanılan dinamik özelliklerin yerini alır.

Her uygulama ayarının benzersiz bir adı olmalıdır. Ad, harf, sayı veya sayı ile başlamamayan alt çizginin herhangi bir birleşimi olabilir ve boşluk içeremez. Ad `Name` özelliği ile değiştirilebilir.

Uygulama ayarları, XML 'e serileştirileya da `ToString` / `FromString` uygulayan bir `TypeConverter` sahip olan herhangi bir veri türü olarak depolanabilir. En yaygın türler `String`, `Integer` ve `Boolean`, ancak değerleri <xref:System.Drawing.Color>, <xref:System.Object> veya bağlantı dizesi olarak da saklayabilirsiniz.

Uygulama ayarları da bir değer içerir. Değer, **Value** özelliği ile ayarlanır ve ayarın veri türüyle eşleşmelidir.

Ayrıca, uygulama ayarları, tasarım zamanında bir formun veya denetimin özelliğine bağlanabilir.

Kapsama göre iki tür uygulama ayarı vardır:

- Uygulama kapsamlı ayarlar, bir Web hizmeti URL 'SI veya bir veritabanı bağlantı dizesi gibi bilgiler için kullanılabilir. Bu değerler uygulamayla ilişkilendirilir. Bu nedenle, kullanıcılar çalışma zamanında bunları değiştiremezler.

- Kullanıcı kapsamlı ayarlar, bir formun veya yazı tipi tercihinin son konumunu kalıcı hale getirme gibi bilgiler için kullanılabilir. Kullanıcılar, çalışma zamanında bu değerleri değiştirebilir.

  **Kapsam** özelliğini kullanarak bir ayarın türünü değiştirebilirsiniz.

  Proje sistemi, uygulama ayarlarını iki XML dosyasında depolar: ilk uygulama ayarını oluştururken tasarım zamanında oluşturulan bir App. config dosyası; ve uygulamayı çalıştıran kullanıcı herhangi bir kullanıcı ayarının değerini değiştirdiğinde çalışma zamanında oluşturulan bir User. config dosyası. Uygulama özellikle bunu yapmak için bir yöntem çağırmadığı takdirde Kullanıcı ayarlarındaki değişikliklerin diske yazılmadığından emin olun.

## <a name="creating-application-settings-at-design-time"></a>Tasarım zamanında uygulama ayarları oluşturma

Tasarım zamanında, uygulama ayarlarını iki şekilde oluşturabilirsiniz: **Proje Tasarımcısı**'nın **Ayarlar** sayfasını veya bir form veya denetim için **Özellikler** penceresini kullanarak bir özelliği bir özelliğe bağlamanıza olanak tanır.

Uygulama kapsamlı bir ayar oluşturduğunuzda (örneğin, bir veritabanı bağlantı dizesi veya sunucu kaynaklarına bir başvuru), [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] `<applicationSettings>` etiketiyle App. config dosyasına kaydeder. (Bağlantı dizeleri `<connectionStrings>` etiketinin altına kaydedilir.)

Kullanıcı kapsamlı bir ayar oluşturduğunuzda (örneğin, varsayılan yazı tipi, giriş sayfası veya pencere boyutu), [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] `<userSettings>` etiketiyle App. config dosyasına kaydeder.

> [!IMPORTANT]
> Bağlantı dizelerini App. config ' de depoladığınızda, bağlantı dizesinde parolalar veya sunucu yolları gibi hassas bilgilerin görüntülenmesinden kaçınmak için önlemler almalısınız.
>
> Bir dış kaynaktan bir kullanıcı KIMLIĞI ve parola sağlayan bir bağlantı dizesi bilgileri alırsanız, Bağlantı dizenizi oluşturmak için kullandığınız değerlerin ek bağlantı dizesi parametreleri içermediğinden emin olmak için dikkatli olmanız gerekir Bu, bağlantınızın davranışını değiştirir.
>
> Yapılandırma dosyasındaki hassas bilgileri şifrelemek için korumalı yapılandırma özelliğini kullanmayı düşünün. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](https://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4) .

> [!NOTE]
> Sınıf kitaplıkları için yapılandırma dosyası modeli olmadığından, sınıf kitaplığı projeleri için uygulama ayarları uygulanmaz. Özel durum, bir yapılandırma dosyası olabilen Office DLL projesi için bir Visual Studio Araçları.

## <a name="using-customized-settings-files"></a>Özelleştirilmiş ayarlar dosyalarını kullanma

Ayar gruplarının kolay yönetimi için projenize özelleştirilmiş ayarlar dosyaları ekleyebilirsiniz. Tek bir dosyada bulunan ayarlar bir birim olarak yüklenir ve kaydedilir. Bu nedenle, ayarları sık kullanılan ve seyrek kullanılan gruplar için ayrı dosyalarda depolayabilmek, ayarları yükleme ve kaydetme sırasında zamandan tasarruf edebilir.

Örneğin, projenize SpecialSettings. Settings gibi bir dosya ekleyebilirsiniz. @No__t_0 sınıfınız `My` ad alanında gösterilmediğinden, **Görünüm kodu** , `Partial Class SpecialSettings` içeren özel ayarlar dosyasını okuyabilir.

Ayarlar Tasarımcısı öncelikle proje sisteminin oluşturduğu Settings. Settings dosyasını arar; Bu, proje Tasarımcısı 'nın **Ayarlar** sekmesinde görüntülediği varsayılan dosyadır. Settings. settings, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projeler Için My projem klasöründe ve [!INCLUDE[csprcs](../includes/csprcs-md.md)] projeleri için özellikler klasöründe bulunur. Proje Tasarımcısı daha sonra projenin kök klasöründeki diğer ayarlar dosyalarını arar. Bu nedenle, özel ayarlar dosyanızı buraya koymanız gerekir. Projeniz başka bir yerde bir. Settings dosyası eklerseniz, proje Tasarımcısı bunu bulamaz.

## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-basic"></a>Visual Basic çalışma zamanında uygulama ayarlarına erişme veya bu ayarları değiştirme

@No__t_0 projelerinde, `My.Settings` nesnesini kullanarak çalışma zamanında uygulama ayarlarına erişebilirsiniz. **Ayarlar sayfasında,** Settings. vb dosyasını görüntülemek Için **kodu görüntüle** düğmesine tıklayın. Settings. vb, ayarlar sınıfında bu olayları işleyebilmenizi sağlayan `Settings` sınıfını tanımlar: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded> ve <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. Settings. vb içindeki `Settings` sınıfının, tüm oluşturulan sınıfın değil yalnızca kullanıcıya ait kodu görüntüleyen kısmi bir sınıf olduğunu unutmayın. @No__t_0 nesnesini kullanarak uygulama ayarlarına erişme hakkında daha fazla bilgi için bkz. [uygulama ayarlarına erişme](https://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e).

Kullanıcının çalışma zamanında değiştiği kullanıcı kapsamlı ayarların değerleri (örneğin, bir formun konumu) bir User. config dosyasında depolanır. Varsayılan değerlerin App. config dosyasına hala kaydedildiğine dikkat edin.

Çalışma zamanında Kullanıcı tanımlı herhangi bir ayarı değiştirdiyseniz, örneğin, uygulamayı test etmek ve bu ayarları varsayılan değerlerine sıfırlamak istiyorsanız, **Synchronize** düğmesine tıklayın.

Ayarlara erişmek için `My.Settings` nesnesini ve default. Settings dosyasını kullanmanızı kesinlikle öneririz. Bunun nedeni, ayarlara Özellikler atamak için ayarlar tasarımcısını kullanabilir ve ek olarak, Uygulama kapanmadan önce Kullanıcı ayarları otomatik olarak kaydedilir. Ancak, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] uygulamanız ayarlara doğrudan erişebilir. Bu durumda, `MySettings` sınıfına erişmeniz ve projenin kökünde özel bir. Settings dosyası kullanmanız gerekir. Uygulama için C# yaptığınız gibi, uygulamayı sonlandırmadan önce Kullanıcı ayarlarını da kaydetmelisiniz; Bu, aşağıdaki bölümde açıklanmıştır.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-c"></a>Visual 'te çalışma zamanında uygulama ayarlarına erişme veya bu ayarları değiştirmeC#
<!-- markdownlint-enable MD003 MD020 -->

@No__t_1 gibi [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] dışındaki dillerde, aşağıdaki [!INCLUDE[csprcs](../includes/csprcs-md.md)] örneğinde gösterildiği gibi `Settings` sınıfına doğrudan erişmeniz gerekir.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Ayrıca, Kullanıcı ayarlarını kalıcı hale getirmek için bu sarmalayıcı sınıfının `Save` yöntemini açıkça çağırmanız gerekir. Bunu genellikle ana formun `Closing` olay işleyicisinde yapabilirsiniz. Aşağıdaki [!INCLUDE[csprcs](../includes/csprcs-md.md)] örnek `Save` yöntemine yapılan çağrıyı gösterir.

```csharp
Properties.Settings.Default.Save();
```

Uygulama ayarlarına `Settings` sınıfı aracılığıyla erişme hakkında genel bilgi için bkz. [uygulama ayarlarına genel bakış](https://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc). Ayarlar arasında yineleme yapma hakkında daha fazla bilgi için bu [Forum gönderisini](http://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral)inceleyin.

## <a name="see-also"></a>Ayrıca Bkz.

- [Uygulama Ayarlarına Erişme](https://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e)
