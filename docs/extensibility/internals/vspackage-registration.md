---
title: VSPackage kaydı | Microsoft Docs
description: paketlerin yüklendikleri Visual Studio ve kayıt defterine bilgi yazarak yüklenmesi gereken vspackage kaydı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f0257eb175dff65a28cc942ef4854cfdff437d5c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117637"
---
# <a name="vspackage-registration"></a>VSPackage Kaydı
VSPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , yüklü olmaları ve yüklenmesi gerektiğini tavsiye etmelidir. Bu işlem, kayıt defterine bilgi yazılarak gerçekleştirilir. Bu, bir yükleyicinin tipik bir işidir.

> [!NOTE]
> Bu, VSPackage geliştirme sırasında kendi kendine kayıt kullanımı için kabul edilen bir uygulamadır. Ancak, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] iş ortakları, kurulum kapsamında kendi ürünlerini kendi kendine kayıt kullanarak teslim edemez.

 Windows Installer paketteki kayıt defteri girdileri genellikle kayıt defteri tablosunda yapılır. Dosya uzantılarını kayıt defteri tablosuna da kaydedebilirsiniz. ancak, Windows Installer programlı tanımlayıcı (progıd), sınıf, uzantı ve fiil tabloları aracılığıyla yerleşik destek sağlar. Daha fazla bilgi için bkz. [veritabanı tabloları](/windows/desktop/Msi/database-tables).

 Kayıt defteri girdlarınızın seçtiğiniz yan yana stratejiniz için uygun olan bileşenle ilişkili olduğundan emin olun. örneğin, paylaşılan bir dosya için kayıt defteri girişleri, bu dosyanın Windows Installer bileşeniyle ilişkilendirilmelidir. Benzer şekilde, sürüme özgü bir dosyanın kayıt defteri girişlerine bu dosyanın bileşeniyle ilişkilendirilmesi gerekir. Aksi halde, VSPackage 'ı bir sürümüne yüklemek veya kaldırmak, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage 'ı diğer sürümlerde bozabilir. Daha fazla bilgi için bkz. [Visual Studio birden çok sürümünü destekleme](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

> [!NOTE]
> Kayıt yönetmenin en kolay yolu, hem geliştirici kaydı hem de yüklenme zamanı kaydı için aynı dosyalardaki verileri kullanmaktır. Örneğin, bazı yükleyici geliştirme araçları derleme zamanında dosyayı. reg biçiminde kullanabilir. Geliştiriciler kendi günlük geliştirme ve hata ayıklama için. reg dosyalarını korumadığında, aynı dosyalar yükleyiciye otomatik olarak dahil edilebilir. Kayıt verilerini otomatik olarak paylaşadıysanız, yükleyicinin kayıt verileri kopyasının güncel olduğundan emin olmanız gerekir.

## <a name="registering-unmanaged-vspackages"></a>Yönetilmeyen VSPackages kaydetme
 yönetilmeyen vspackages (Visual Studio paketi şablonu tarafından oluşturulanlar dahil), kayıt bilgilerini depolamak için ATL stili. rgs dosyalarını kullanır. . RGS dosya biçimi, ATL 'ye özeldir ve genellikle bir yükleme yazma aracı tarafından olduğu gibi tüketilemez. VSPackage yükleyicisi için kayıt bilgileri ayrı olarak sağlanmalıdır. Örneğin, geliştiriciler dosyaları. reg biçiminde. RGS dosya değişiklikleriyle eşitlenmiş halde tutar. . Reg dosyaları geliştirme çalışması için RegEdit ile birleştirilebilir veya bir yükleyici tarafından tüketilebilir.

## <a name="registering-managed-vspackages"></a>Yönetilen VSPackages 'yi kaydetme
 RegPkg Aracı, yönetilen bir VSPackage 'daki kayıt özniteliklerini okur ve bilgileri doğrudan kayıt defterine yazabilir veya bir yükleyici tarafından tüketilen. reg-format dosyalarını yazabilir.

> [!NOTE]
> RegPkg aracı yeniden dağıtılabilir değildir ve kullanıcının sistemine VSPackage kaydetmek için kullanılamaz.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Neden VSPackages, yüklemesi sırasında Self-Register olmamalıdır
 VSPackage yükleyicileriniz kendi kendine kayda dayanmamalıdır. İlk bakışta, VSPackage 'un kayıt defteri değerlerinin yalnızca VSPackage içinde tutulması iyi bir fikir gibi görünüyor. Geliştiricilerin rutin iş ve test için kullanılabilir kayıt defteri değerlerine ihtiyacı verildiğinden, yükleyicideki kayıt defteri verilerinin ayrı bir kopyasının korunmasından kaçınmak mantıklı olur. Yükleyici, kayıt defteri değerlerini yazmak için VSPackage 'un kendisini kullanır.

 Teorik olarak, kendi kendine kayıt, VSPackage yüklemesine uygun olmayan birçok kusura sahiptir:

- Yükleme, kaldırma, yükleme geri alma ve kaldırma geri alma işlemlerini doğru şekilde desteklemek için, RegPkg çağırarak kendinden kaydeden her yönetilen VSPackage için dört özel eylem yazmanızı gerektirir.

- Yan yana desteğe yaklaşımda, desteklenen her sürümü için RegSvr32 veya RegPkg komutunu çağıran dört özel eylem yazarınızın olması gerekebilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- Kendi kendine kayıtlı anahtarların başka bir özellik veya uygulama tarafından kullanıldığını söyleyen bir yöntem olmadığından, kendi kendine kayıtlı modüllerle yükleme güvenli bir şekilde geri alınamaz.

- Otomatik olarak kaydedilen dll 'Ler bazen mevcut olmayan veya yanlış sürümde olan yardımcı DLL 'lere bağlanır. buna karşılık Windows Installer, sistemin geçerli durumuna bağımlılığı olmadan kayıt defteri tablolarını kullanarak dll 'leri kaydedebilir.

- Bir bileşen hem kaynak olarak çalıştır hem de SelfReg tablosunda listeleniyorsa, kendi kendine kayıt kodu tür kitaplıkları gibi ağ kaynaklarına erişimi reddedilebilir. Bu, bileşen yüklemesinin yönetim yüklemesi sırasında başarısız olmasına neden olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Yönetilen paket kaydı](/previous-versions/bb166783(v=vs.100))