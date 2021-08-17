---
title: Windows Yükleyici temel bilgileri | Microsoft Docs
description: VSPackage Windows vsPackage bileşenlerinde düzenleme de dahil olmak üzere vsPackage yüklemede kullanmak üzere Windows öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 34e36e5ff7be09c12781c18e8f4d7c842a357c6e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041821"
---
# <a name="windows-installer-basics"></a>Temel Windows Installer Bilgileri
Windows Yükleyicisi, bir kullanıcının bilgisayarına uygulama veya yazılım ürünlerini yükp kaldırır ve bu görevleri Windows Yükleyici bileşenleri (bazen WIC veya yalnızca bileşenler olarak da adlandırılan) birimlerde gerçekleştirerek gerçekleştirebilir. GUID, her WIC'i tanımlar. Bu, Windows Installer kullanılarak yapılan kurulumlar için temel yükleme ve başvuru sayma birimidir.

 Windows Yükleyicisi'nin kapsamlı belgeleri için Platform SDK'sı konusuna Windows [bakın.](/previous-versions/2kt85ked(v=vs.120))

## <a name="authoring-a-vspackage"></a>VSPackage Yazma
 Windows Yükleyici, bir ürünü yüklemek, kaldırmak Windows onarmak ve kurulum kullanıcı arabirimini (UI) çalıştırmak için gereken bilgileri içeren yükleme paketlerini kullanır. Her yükleme paketi, .msi veritabanı, özet bilgi akışı ve yüklemenin çeşitli bölümlerine ilişkin veri akışlarını içeren bir dosya içerir. Yükleyiciyi kullanmak için bir yükleme yazmalısınız. Yükleyici, yüklemeleri bileşenler kavramına göre düzenleyemediklerinden ve yüklemeyle ilgili bilgileri ilişkisel bir veritabanında depolasa da, yükleme paketi yazma işlemi geniş kapsamlı olarak aşağıdaki adımları içerir:

1. Sürüm ve yan yana stratejilerinizi desteklemek için kurulum yazmanızı planla.

2. Kullanıcılara sunulacak özellikleri belirleme.

3. VSPackage ve bağımlılıkları bileşenlerde düzenleme.

4. Yükleme veritabanını bilgilerle doldurmak.

5. Yükleme paketini doğrulama.

   Bu belge öncelikli olarak sürecin ilk ve üçüncü adımlarıyla ilgilidir. Bu adımlar sırasında VSPackage özelliklerinizi WIC'ler olarak düzenleyecek ve böylece sürüm ve hizmet stratejinizi sonraki sürümlerini hesaba ekleyecek şekilde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çerçevelersiniz. Kalan üç adım, Platform SDK'sı Windows Yükleyicisi belgelerinde ayrıntılı olarak ele alınmaktadır.

## <a name="key-terms"></a>Önemli Terimler
 Aşağıda, Windows Yükleyicisi teknolojisiyle ilgili önemli terimlerin tanımları ve açıklamalarını içerir.

 Kaynak Dosyaları, kayıt defteri anahtarları, kısayollar veya başka bir şey bilgisayara yüklenmiş olabilir. Bu kaynaklar, Yükleyici bileşenlerine Windows gruplandı.

 Windows Yükleyici bileşeni (WIC) Bir birim olarak yüklenmiş ve kaldırdığınız ilgili kaynakların mantıksal bir grubunu temsil eden temel yükleme birimi. Windows Yükleyici bileşenleri benzersiz bir bileşen kimliği veya GUID ile tanımlanır. Ayrıca, Windows Yükleyicisi başvuru saymayı WIC düzeyinde sürdürür. En yüksek sürüm oluşturma esnekliği için, belirli bir WIC'ye DLL gibi birden fazla birincil kaynak dahil edin. WiC'yi tanımp doldurmak, GUID vermek ve dağıtmak için bileşimini değiştiremezsiniz. Daha fazla bilgi için [bkz. Uygulamaları Bileşenlerde Düzenleme.](/windows/desktop/Msi/organizing-applications-into-components)

 Paket (Redist paketi) Bu dosyanın işaret .msi dış kaynak dosyalardan oluşan bir dağıtım birimi. Paket, Kullanıcı Arabirimini çalıştırmak Windows ve uygulamayı yüklemek veya kaldırmak için gereken tüm bilgileri içerir.

 .msi Dosya Bir uygulamayı yüklemek için gereken yönergeleri ve verileri içeren COM yapılandırılmış bir depolama dosyası. Her paket en az bir dosya .msi içerir. Bu .msi yükleyici veritabanını, bir özet bilgi akışını ve muhtemelen bir veya daha fazla dönüştürmeyi ve iç kaynak dosyasını içerir. Yük uygulanacak dosyalar bir kabinde sıkıştırılabilir ve .msi dosyasındaki bir akışta depolanılabilir ya da kaynak ortamdaki .msi dışında depolanmış, sıkıştırılmış veya sıkıştırılmamış olabilir. Daha fazla bilgi için [bkz. Windows Yükleyici Dosya Uzantıları.](/windows/desktop/Msi/windows-installer-file-extensions)

## <a name="windows-installer-rules-enforcement"></a>Windows Yükleyici Kurallarını Zorlama
 İki kural kümesi, kurulum bileşenleri aracılığıyla kaynakların dağıtımını belirler. Bir kural kümesi, Windows Yükleyicisi tarafından korunurken, ikinci kümeyi yükleme yazarı olarak zorlamalısınız.

> [!NOTE]
> Windows Yükleyicisi kurallarının zorlaması, yalnızca dosyanız için bir doğrulama .msi oluşur. Yine de, bu kuralları en iyi yöntemler olarak kabul etmek için uyarıldık. Daha fazla bilgi için, [bkz. Validating an Installation Database](/windows/desktop/Msi/validating-an-installation-database) and [Package Validation](/windows/desktop/Msi/package-validation).

#### <a name="installer-enforced-rules"></a>Installer-Enforced Kuralları

- Bir bileşende yer alan tüm dosyaların aynı dizine yüklenmiş olması gerekir. Buna karşılık, ayrı klasörlere yüklenmiş dosyaların ayrı bileşenlere ait olması gerekir.

- Bileşen başına yalnızca bir anahtar yol olabilir. Anahtar yolu, bileşenin tamamını temsil eden bir dosya veya kayıt defteri anahtarıdır.

#### <a name="component-provider-responsibilities"></a>Component-Provider Sorumlulukları

- Sonraki sürümlerde ayrı gönderilebilir iki kaynak ayrı bileşenlerde yer amalıdır. Kaynaklar yalnızca bu kaynakların hiçbir zaman ayrı olarak gönderilemayacakları kesin olduğunda aynı bileşende gruplamalıdır. Aslında, tüm birincil kaynakların (örneğin, URL'ler) her zaman ayrı WIC'lerde mevcut olması önerilir. Daha fazla bilgi için bkz. [Yükleyici Bileşenlerini Tanımlama.](/windows/desktop/Msi/defining-installer-components)

- Hiçbir sürüme sahip kaynak birden fazla WIC'de sevk edilemez.

## <a name="see-also"></a>Ayrıca bkz.
- [Bileşen Kuralları Bozuksa Ne Olur?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)
