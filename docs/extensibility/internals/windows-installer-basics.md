---
title: Windows Installer temel bilgiler | Microsoft Docs
description: VSPackage özelliklerinizi Windows Installer bileşenlere düzenleme da dahil olmak üzere VSPackage yükleme konusunda Windows Installer hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4081c79b7492e369e19187a099bf975275cb371c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869498"
---
# <a name="windows-installer-basics"></a>Temel Windows Installer Bilgileri
Windows Installer, bir kullanıcının bilgisayarındaki uygulamaları veya yazılım ürünlerini yükleyip kaldırır ve bu görevleri, Windows Installer bileşenleri olarak adlandırılan birimlerde (bazen WICs veya yalnızca bileşenler olarak adlandırılır) gerçekleştirerek. Bir GUID, Windows Installer kullanarak kurulumların temel yükleme birimi ve başvuru sayımı olan her bir WIC 'yi tanımlar.

 Windows Installer kapsamlı belgeler için, [Windows Installer](/previous-versions/2kt85ked(v=vs.120))Platform SDK konusuna bakın.

## <a name="authoring-a-vspackage"></a>VSPackage yazma
 Windows Installer, Windows Installer bir ürünü yüklemesi, kaldırması veya onarması ve kurulum Kullanıcı arabirimini (UI) çalıştırmak için gereken bilgileri içeren yükleme paketlerini kullanır. Her yükleme paketi, yükleme veritabanı, Özet bilgi akışı ve yüklemenin çeşitli bölümleri için veri akışları içeren bir. msi dosyası içerir. Yükleyiciyi kullanmak için bir yükleme yazmanız gerekir. Yükleyici, kurulumları bileşen kavramı etrafında düzenler ve yükleme hakkındaki bilgileri bir ilişkisel veritabanında depoladığından, yükleme paketi yazma işlemi aşağıdaki adımları büyük ölçüde kapsar:

1. Sürüm oluşturma ve yan yana stratejilerinizi desteklemek için kurulum yazma planınızı planlayın.

2. Kullanıcılara sunulacak özellikleri belirler.

3. VSPackage ve bağımlılıkları bileşenlere göre düzenleyin.

4. Yükleme veritabanını bilgilerle doldurun.

5. Yükleme paketini doğrulayın.

   Bu belge, öncelikle işlemin birinci ve üçüncü adımlarıyla ilgilidir. Bu adımlar boyunca VSPackage özelliklerinizi WICs olarak düzenlersiniz, bu sayede sürüm oluşturma ve bakım stratejinizi sonraki sürümlerini hesaba katıyabilmenizi sağlayabilirsiniz [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Kalan üç adım, Platform SDK 'sindeki Windows Installer belgelerinde ayrıntılı olarak ele alınmıştır.

## <a name="key-terms"></a>Anahtar terimleri
 Aşağıda Windows Installer teknolojisiyle ilgili temel koşulların tanımları verilmiştir.

 Kaynak dosyaları, kayıt defteri anahtarları, kısayollar veya vb. bir bilgisayara yüklenebilir. Bu kaynaklar mantıksal olarak Windows Installer bileşenleri halinde gruplandırılır.

 Windows Installer Component (WIC) bir birim olarak yüklenen ve kaldırılan ilgili kaynakların mantıksal bir gruplandırmasını temsil eden temel yükleme birimidir. Windows Installer bileşenleri, benzersiz bir bileşen KIMLIĞI veya GUID ile tanımlanır. Ayrıca, Windows Installer, WIC düzeyinde başvuru sayımını tutar. En yüksek sürüm oluşturma esnekliği için, belirli bir WIC 'de DLL gibi birden fazla birincil kaynak dahil edin. Bir WIC 'yi tanımladıktan ve doldurduktan, bir GUID 'ye vermenize ve dağıtmanıza sonra, kompozisyonunu değiştiremeyiz. Daha fazla bilgi için bkz. [uygulamaları bileşenlere düzenleme](/windows/desktop/Msi/organizing-applications-into-components).

 Package (REDIST paketi) Bu dosyanın işaret edebileceği bir. msi dosyası ve harici kaynak dosyalarından oluşan bir dağıtım birimi. Bir paket, Windows Installer Kullanıcı arabirimini çalıştırmak ve uygulamayı yüklemek ya da kaldırmak için gereken tüm bilgileri içerir.

 . msi dosyası bir uygulamayı yüklemek için gereken yönergeleri ve verileri içeren COM ile yapılandırılmış bir depolama dosyası. Her pakette en az bir. msi dosyası bulunur. . Msi dosyası yükleyici veritabanını, bir özet bilgi akışını ve muhtemelen bir veya daha fazla dönüşümleri ve iç kaynak dosyalarını içerir. Yüklenecek dosyalar bir dolapta sıkıştırılabilir ve. msi dosyasındaki bir akışta depolanabilir veya kaynak ortamdaki. msi dosyasının dışında,. msi dosyasında depolanabilir, sıkıştırılır veya sıkıştırılmamış olabilir. Daha fazla bilgi için bkz. [Windows Installer dosya uzantıları](/windows/desktop/Msi/windows-installer-file-extensions).

## <a name="windows-installer-rules-enforcement"></a>Windows Installer kuralları zorlaması
 İki kural kümesi, kurulum 'un bileşenleri aracılığıyla kaynakların dağıtımını belirler. Bir kural kümesi Windows Installer kendisi tarafından korunur, ancak ikinci kümeyi yükleme yazarı olarak zorlamalısınız.

> [!NOTE]
> Windows Installer kuralları zorlaması yalnızca. msi dosyanızın doğrulanmasını çalıştırırsanız oluşur. Bununla birlikte, bu kuralları en iyi uygulamalar olarak değerlendirmek için dikkatli olmanız gerekir. Daha fazla bilgi için bkz. [yükleme veritabanını](/windows/desktop/Msi/validating-an-installation-database) ve [paket doğrulamasını doğrulama](/windows/desktop/Msi/package-validation).

#### <a name="installer-enforced-rules"></a>Installer-Enforced kuralları

- Belirli bir bileşendeki tüm dosyaların aynı dizine yüklenmesi gerekir. Buna karşılık, ayrı klasörlere yüklenen dosyalar ayrı bileşenlere ait olmalıdır.

- Bileşen başına yalnızca bir anahtar yolu olabilir. Anahtar yolu, tüm bileşeni temsil eden bir dosya veya kayıt defteri anahtarıdır.

#### <a name="component-provider-responsibilities"></a>Component-Provider sorumlulukları

- Sonraki sürümlerde ayrı olarak sevk edebilen tüm iki kaynak ayrı bileşenlerde bulunmalıdır. Kaynakların aynı bileşen halinde gruplanmaması gerekir, ancak bu kaynakların hiçbir zaman ayrı olarak teslim etmeyeceğinden emin olmalısınız. Aslında, tüm birincil kaynakların (örneğin, dll 'Ler) her zaman ayrı WCS 'lerde mevcut olması önerilir. Daha fazla bilgi için bkz. [Yükleyici bileşenlerini tanımlama](/windows/desktop/Msi/defining-installer-components).

- Hiç sürümlü kaynak hiçbir zaman birden fazla WIC içinde teslim edilmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Bileşen kuralları bozulur ne olur?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)
