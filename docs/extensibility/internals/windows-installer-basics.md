---
title: Windows Yükleyici Temelleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aeea0b17a3c234bb7670642fb9ae0a442c9d60cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703411"
---
# <a name="windows-installer-basics"></a>Temel Windows Installer Bilgileri
Windows Installer, uygulamaları veya yazılım ürünlerini kullanıcının bilgisayarına yükler ve yükler ve yükler, bu görevleri Windows Installer bileşenleri (bazen WIC veya yalnızca bileşenler olarak da adlandırılır) adı verilen birimlerde gerçekleştirir. GUID, Windows Installer kullanan kurulumlar için temel yükleme ve başvuru sayımı birimi olan her WIC'yi tanımlar.

 Windows Yükleyici'nin kapsamlı belgeleri için, Platform SDK konusu olan [Windows Installer'a](/previous-versions/2kt85ked(v=vs.120))bakın.

## <a name="authoring-a-vspackage"></a>VSPackage yazma
 Windows Installer, Windows Installer'ın bir ürünü yüklemesi, kaldırması veya onarması ve kurulum kullanıcı arabirimini (UI) çalıştırması gereken bilgileri içeren yükleme paketleri kullanır. Her yükleme paketi, yükleme veritabanı, özet bilgi akışı ve yüklemenin çeşitli bölümleri için veri akışları içeren bir .msi dosyası içerir. Yükleyiciyi kullanmak için bir yükleme yazmanız gerekir. Yükleyici yüklemeleri bileşenler kavramı etrafında düzenlediğinden ve yükleme yle ilgili bilgileri ilişkisel bir veritabanında depoladığından, yükleme paketi yazma işlemi genel olarak aşağıdaki adımları içerir:

1. Sürüm ve yan yana stratejilerinizi desteklemek için kurulumunuzu yazarak planlayın.

2. Kullanıcılara sunulacak özellikleri tanımlayın.

3. VSPackage'ı ve bağımlılıkları bileşenler halinde düzenleyin.

4. Yükleme veritabanını bilgilerle doldurun.

5. Yükleme paketini doğrulayın.

   Bu dokümantasyon öncelikle sürecin birinci ve üçüncü adımları ile ilgilidir. Bu adımlar sırasında VSPackage özelliklerinizi WIC'lerde düzenlersiniz, böylece sürüm ve servis stratejinizi sonraki sürümlerini hesaba katmak için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]çerçeveleyebilirsiniz. Geri kalan üç adım, Platform SDK'daki Windows Installer belgelerinde ayrıntılı olarak ele alınmıştır.

## <a name="key-terms"></a>Anahtar Terimler
 Aşağıda Windows Installer teknolojisiyle ilgili anahtar terimlerin tanımları verilmiştir.

 Kaynak Dosyaları, kayıt defteri anahtarları, kısayollar, ya da benzeri bir bilgisayara yüklenebilir. Bu kaynaklar mantıksal olarak Windows Installer bileşenlerine gruplandırılır.

 Windows Installer bileşeni (WIC) Yüklenmiş ve bir birim olarak kaldırılan ilgili kaynakların mantıksal bir gruplandırmasını temsil eden temel yükleme birimi. Windows Installer bileşenleri benzersiz bir bileşen kimliği veya GUID ile tanımlanır. Ayrıca, Windows Installer wic düzeyinde referans sayma korur. Maksimum sürüm esnekliği için, belirli bir WIC'de DLL gibi en fazla bir birincil kaynak ekleyin. Bir WIC'yi tanımlayıp doldurup doldurup guid verdikten ve dağıttıktan sonra kompozisyonunu değiştiremeyeceğiniz dikkat edin. Daha fazla bilgi için [bkz.](/windows/desktop/Msi/organizing-applications-into-components)

 Paket (Redist paketi) .msi dosyası ve bu dosyanın işaret edebileceği dış kaynak dosyalarından oluşan bir dağıtım birimi. Paket, Windows Installer kullanıcı aylığını çalıştırmak ve uygulamayı yüklemek veya kaldırmak için gereken tüm bilgileri içerir.

 .msi Dosya Bir uygulama yüklemek için gerekli yönergeleri ve verileri içeren BIR COM yapılandırılmış depolama dosyası. Her paket en az bir .msi dosyası içerir. .msi dosyası yükleyici veritabanını, özet bilgi akışını ve muhtemelen bir veya daha fazla dönüşüm ve iç kaynak dosyasını içerir. Yüklenecek dosyalar bir dolaba sıkıştırılabilir ve .msi dosyasındaki bir akışta depolanabilir veya kaynak ortamdaki .msi dosyasının dışında depolanabilir, sıkıştırılabilir veya sıkıştırılmamış olarak depolanabilir. Daha fazla bilgi için [Windows Installer Dosya Uzantıları'na](/windows/desktop/Msi/windows-installer-file-extensions)bakın.

## <a name="windows-installer-rules-enforcement"></a>Windows Installer Kuralları Zorlama
 İki kural kümesi, kurulumunuzun bileşenleri aracılığıyla kaynakların dağıtımını belirler. Bir kural kümesi Windows Yükleyici'nin kendisi tarafından korunur, ikinci kümeyi yükleme yazarı olarak zorlamanız gerekir.

> [!NOTE]
> Windows Installer kurallarının uygulanması yalnızca .msi dosyanızın doğrulaması çalıştırdığınızda oluşur. Yine de, bu kuralları en iyi uygulamalar olarak ele almak için uyarılır. Daha fazla bilgi için yükleme [veritabanını ve](/windows/desktop/Msi/validating-an-installation-database) [Paket Doğrulamayı](/windows/desktop/Msi/package-validation)doğrulama ya da doğrulama'ya bakın.

#### <a name="installer-enforced-rules"></a>Yükleyici-Zorla Zorunlu Kurallar

- Belirli bir bileşendeki tüm dosyaların aynı dizine yüklenmesi gerekir. Tersine, ayrı klasörlere yüklenen dosyalar ayrı bileşenlere ait olmalıdır.

- Bileşen başına yalnızca bir anahtar yolu olabilir. Anahtar yol, yalnızca tüm bileşeni temsil eden bir dosya veya kayıt defteri anahtarıdır.

#### <a name="component-provider-responsibilities"></a>Bileşen Sağlayıcı Sorumlulukları

- Sonraki sürümlerde ayrı olarak sevk olabilecek iki kaynak ayrı bileşenlerde bulunmalıdır. Kaynaklar, yalnızca bu kaynakların hiçbir zaman ayrı olarak sevk edilmeyeceğinden emin olduğunuzda aynı bileşende gruplandırılmalıdır. Aslında, tüm birincil kaynakların (Örneğin, DL'ler) her zaman ayrı WIC'lerde bulunması önerilir. Daha fazla bilgi için [installer bileşenlerini tanımlama](/windows/desktop/Msi/defining-installer-components)ya da tanımlama 'ya bakın.

- Hiçbir sürümlü kaynak birden fazla WIC'de gönderilmemelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Bileşen Kuralları Bozulursa Ne Olur?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)
