---
title: Hataları giderme (ClickOnce dağıtımları)
description: Bu makalede, bir ClickOnce uygulaması dağıtırken ortaya çıkabilir ve her sorunu çözme adımları açıklanmıştır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.UncRequired
- Microsoft.VisualStudio.Publish.ClickOnceProvider.ErrorPrompt.NoInstallUrl
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications, ClickOnce
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
ms.assetid: 22dfe8f1-8271-4708-9c25-6bbb13920ac8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 4cfbfa1c13a6006303b1fd0fa164d78c7f4e6b9f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089829"
---
# <a name="troubleshoot-specific-errors-in-clickonce-deployments"></a>ClickOnce dağıtımları içinde belirli hataları giderme
Bu makalede, bir uygulamayı dağıtırken ortaya çıkabilir aşağıdaki yaygın hatalar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] liste ve her sorunu çözmek için adımlar sağlar.

## <a name="general-errors"></a>Genel hatalar

#### <a name="when-you-try-to-locate-an-application-file-nothing-occurs-or-xml-renders-in-internet-explorer-or-you-receive-a-run-or-save-as-dialog-box"></a>Bir uygulama dosyasını bulmaya çalışsanız hiçbir şey olmaz veya XML Internet Explorer veya Farklı Çalıştır iletişim kutusu alırsınız
 Bu hata büyük olasılıkla içerik türlerinin (MIME türleri olarak da bilinir) sunucuda veya istemcide doğru şekilde kaydedilememelerinden kaynaklandır.

 İlk olarak, sunucunun *.application* uzantısını "application/x-ms-application" içerik türüyle ilişkilendirmek üzere yapılandırıldığından emin olun.

 Sunucu doğru yapılandırıldıysa, bilgisayarınızda .NET Framework 2.0'ın yüklü olup olmadığını denetleyin. .NET Framework 2.0 yüklüyse ve bu sorunu görmeye devam ediyorsanız, içerik türünü istemciye yeniden kaydetmek için .NET Framework 2.0'ı kaldırıp yeniden yüklemeyi deneyin.

#### <a name="error-message-says-unable-to-retrieve-application-files-missing-in-deployment-or-application-download-has-been-interrupted-check-for-network-errors-and-try-again-later"></a>Hata iletisi şöyledir: "Uygulama alınamadı. Dağıtımda eksik dosyalar" veya "Uygulama indirme kesintiye uğradı, ağ hatalarını denetleyin ve daha sonra yeniden deneyin"
 Bu ileti, bildirim tarafından başvurulan bir veya daha fazla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dosyanın indirilenenem olduğunu gösterir. Bu hatada hata ayıklamanın en kolay yolu, indirileyebilen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] URL'yi indirmeyi denemektir. Olası bazı nedenler:

- Günlük dosyasında "(403) Yasak" veya "(404) Bulunamadı" yazıyorsa, Web sunucusunun yapılandırıldığından emin olun. Daha fazla bilgi için [bkz. Dağıtımlarda Sunucu ve ClickOnce Sorunları.](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)

- .config *dosyası* sunucu tarafından engellenmişse, bu makalenin devamlarında "Bir .config dosyası olan bir uygulamayı yüklemeye çalışsanız hata [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] indir" bölümüne bakın.

- Dağıtım bildiriminde URL etkinleştirme için kullanılan URL'den farklı bir konuma işaret ettiği için `deploymentProvider` bu hatanın olup olmadığını belirler.

- Tüm dosyaların sunucuda mevcut olduğundan emin olun; [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] günlük size hangi dosyanın bulunamadı gerektiğini söylemeli.

- Ağ bağlantısı sorunları olup olmadığını denetleyin; İndirme sırasında istemci bilgisayarınız çevrimdışıysa bu iletiyi alabilirsiniz.

#### <a name="download-error-when-you-try-to-install-a-clickonce-application-that-has-a-config-file"></a>.config dosyası olan bir ClickOnce uygulamayı yükleme sırasında .config indirme
 Varsayılan olarak, Visual Basic Windows tabanlı bir uygulama bir App.config içerir. Bir kullanıcı Windows Server 2003 kullanan bir Web sunucusundan yükleme yapmaya çalıştığında bir sorun olur çünkü bu işletim sistemi güvenlik *nedenleriyle*.configyüklemesini engeller. Dosyanın *.config* etkinleştirmek için Yayımlama Seçenekleri iletişim kutusunda **".deploy" dosya uzantısını** **kullan'a** tıklayın.

 Ayrıca içerik türlerini (MIME türleri olarak da bilinir) .application, .manifest ve .deploy dosyaları için uygun şekilde ayarlamanız gerekir. Daha fazla bilgi için Web sunucusu belgelerinize bakın.

 Daha fazla bilgi için, sunucu ve Windows dağıtımlarında istemci yapılandırma sorunları içinde "Windows Server 2003: [Kilitli İçerik Türleri" ClickOnce bakın.](../deployment/server-and-client-configuration-issues-in-clickonce-deployments.md)

#### <a name="error-message-application-is-improperly-formatted-log-file-contains-xml-signature-is-invalid"></a>Hata iletisi: "Uygulama yanlış biçimlendirildi;" Günlük dosyası "XML imzası geçersiz" içeriyor
 Bildirim dosyasını güncelleştirilir ve yeniden imzalarsınız. kullanarak veya kullanarak Mage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yeniden yayımla.

#### <a name="you-updated-your-application-on-the-server-but-the-client-does-not-download-the-update"></a>Uygulamayı sunucuda güncelleştirmişsiniz ancak istemci güncelleştirmeyi indirmez
 Bu sorun aşağıdaki görevlerden biri tamamlayarak çözülebilir:

- Dağıtım `deploymentProvider` bildiriminde URL'yi inceleme. Bitleri, aynı konumda ve bu konuma göre `deploymentProvider` güncelleştirin.

- Dağıtım bildiriminde güncelleştirme aralığını doğrulayın. Bu aralık, altı saatte bir gibi düzenli aralıklara ayarlanırsa, bu aralık geçene kadar bir güncelleştirme [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] taraması olmaz. Uygulama her başlatıldığında güncelleştirmeyi taramak için bildirimi değiştirebilirsiniz. Güncelleştirme aralığını değiştirmek, geliştirme sırasında güncelleştirmelerin yük olduğunu doğrulamak için kullanışlı bir seçenektir, ancak uygulama etkinleştirmeyi yavaşlatıyor.

- Uygulamayı uygulamanın ilk çalışma Başlat menüsü. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] güncelleştirmeyi arka planda algımış olabilir, ancak sonraki etkinleştirmede bitleri yüklemeniz istenecek.

#### <a name="during-update-you-receive-an-error-that-has-the-following-log-entry-the-reference-in-the-deployment-does-not-match-the-identity-defined-in-the-application-manifest"></a>Güncelleştirme sırasında şu günlük girdisini içeren bir hata alırsınız: "Dağıtımda başvuru, uygulama bildiriminde tanımlanan kimlikle eşle değil"
 Bu hata, dağıtım ve uygulama bildirimlerini el ile düzenleyemediniz ve bir bildirimde derlemenin kimliğinin açıklamasının diğer bildirimle eşitnin dışında gerçekleşmesine neden olduğu için oluşabilir. Derlemenin kimliği adı, sürümü, kültürü ve ortak anahtar belirteclerinden oluşur. Bildirimlerinizin kimlik açıklamalarını inceler ve farkları düzeltin.

#### <a name="first-time-activation-from-local-disk-or-cd-rom-succeeds-but-subsequent-activation-from-start-menu-does-not-succeed"></a>Yerel diskten veya CD-ROM'dan ilk kez etkinleştirme başarılı olur, ancak Başlat Menüsünden sonraki etkinleştirme başarılı olmaz
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , uygulama güncelleştirmelerini almak için Dağıtım Sağlayıcısı URL'sini kullanır. URL'nin işaret etmekte olduğu konumun doğru olduğunu doğrulayın.

#### <a name="error-cannot-start-the-application"></a>Hata: "Uygulama başlatıla değil"
 Bu hata iletisi genellikle bu uygulamayı mağazaya yüklerken bir sorun olduğunu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] gösterir. Uygulamanın bir hatası var veya depo bozuk. Günlük dosyası size hatanın nerede olduğunu söyler.

 Şunları gerçekleştirin:

- Dağıtım bildiriminin kimliğinin, uygulama bildiriminin kimliğinin ve ana uygulama EXE kimliğinin benzersiz olduğunu doğrulayın.

- Dosya yollarınızı 100 karakterden uzun olmadığını doğrulayın. Uygulamanız çok uzun dosya yolları içeriyorsa depolayabilirsiniz maksimum yol sınırlamalarını aşabilirsiniz. Yolları kısaltmayı ve yeniden yüklemeyi deneyin.

#### <a name="privatepath-settings-in-application-config-file-are-not-honored"></a>Uygulama yapılandırma dosyasındaki PrivatePath ayarlarına onay yok
 PrivatePath (Fusion yoklama yolları) kullanmak için uygulamanın tam güven iznini isteğine sahip olması gerekir. Uygulama bildirimini tam güven isteğine göre değiştirmeyi deneyin ve sonra yeniden deneyin.

#### <a name="during-uninstall-a-message-appears-saying-failed-to-uninstall-application"></a>Kaldırma sırasında "Uygulama kaldırılamadı" iletisi görüntülenir
 Bu ileti genellikle uygulamanın zaten kaldırılmış veya deponun bozuk olduğunu gösterir. Tamam'a **tıklarken** **Program Ekle/Kaldır** girdisi kaldırılır.

#### <a name="during-installation-a-message-appears-that-says-that-the-platform-dependencies-are-not-installed"></a>Yükleme sırasında, platform bağımlılıkları yüklü olmadığını söyleyen bir ileti görüntülenir
 GaC'de (genel derleme önbelleği) uygulamanın çalışması için gereken bir önkoş eksik.

## <a name="publishing-with-visual-studio"></a>Visual Studio ile yayımlama

#### <a name="publishing-in-visual-studio-fails"></a>Visual Studio yayımlama başarısız oluyor
 Hedefledkniz sunucuda yayımlama hakkına sahip olduğundan emin olun. Örneğin, bir terminal sunucusu bilgisayarına yönetici olarak değil normal bir kullanıcı olarak oturum açtıysanız büyük olasılıkla yerel Web sunucusunda yayımlamak için gereken haklara sahip olmazsınız.

 Url ile yayımıyorsanız, hedef bilgisayarda FrontPage Sunucu Uzantıları'nın etkinleştirildiğinden emin olun.

#### <a name="error-message-unable-to-create-the-web-site-site-the-components-for-communicating-with-frontpage-server-extensions-are-not-installed"></a>Hata iletisi: 'Web sitesi \<site> oluşturulamıyor. FrontPage Sunucu Uzantıları ile iletişim kurmak için bileşenler yüklenmez.
 Yayımlamakta Microsoft Visual Studio Web Yazma Bileşeni'nin yüklü olduğundan emin olmak. Express kullanıcıları için bu bileşen varsayılan olarak yüklenmez. Daha fazla bilgi için bkz. [http://go.microsoft.com/fwlink/?LinkId=102310](https://support.microsoft.com/help/945358).

#### <a name="error-message-could-not-find-file-microsoftwindowscommon-controls-version6000-culture-publickeytoken6595b64144ccf1df-processorarchitecture-typewin32"></a>Hata iletisi: 'Microsoft dosyası bulunamıyor. Windows. Common-Controls, Version=6.0.0.0, Culture=*, PublicKeyToken=6595b64144ccf1df, ProcessorArchitecture= \* , Type=win32'
 Görsel stilleri etkinleştirilmiş bir WPF uygulaması yayımlamaya çalışırken bu hata iletisi görüntülenir. Bu sorunu çözmek için [bkz. Nasıl Etkinleştirilmiş Görsel Stiller ile WPF Uygulaması Yayımlama.](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)

## <a name="using-mage"></a>Mage

#### <a name="you-tried-to-sign-with-a-certificate-in-your-certificate-store-and-a-received-blank-message-box"></a>Sertifika deponuza bir sertifika ile oturum açma denemesi ve boş ileti kutusu
 İmzalama **iletişim** kutusunda şunları gerekir:

- Depolanan **bir sertifikayla imzala'ya ve**

- Listeden bir sertifika seçin; İlk sertifika varsayılan seçim değildir.

#### <a name="clicking-the-dont-sign-button-causes-an-exception"></a>"İmzala" düğmesine tıklamak özel durumlara neden oluyor
 Bu sorun bilinen bir hatadır. Tüm [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bildirimlerin imzaya sahip olması gerekir. İmzalama seçenekleri arasında seçim yaptıktan sonra Tamam'a **tıklayın.**

## <a name="additional-errors"></a>Ek hatalar
 Aşağıdaki tabloda, bir istemci-bilgisayar kullanıcı bir uygulama yükleyene kadar bazı yaygın hata iletileri [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yer alır. Her hata iletisi, hatanın en olası nedeninin açıklamasının yanında listelenir.

| Hata iletisi | Açıklama |
| - | - |
| Uygulama başlatılamay. Uygulama yayımcısı ile iletişime geçin.<br /><br /> Uygulama başlatamaz. Yardım için uygulama satıcısına başvurun. | Bunlar, uygulama başlatılamaysa ve başka bir neden bulunamazsa oluşan genel hata iletileridir. Bu durum genellikle uygulamanın bir şekilde bozuk olduğu veya deponun [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bozuk olduğu anlamına gelir. |
| Devam etmek yok. Uygulama yanlış biçimlendirildi. Yardım almak için uygulama yayımcısına başvurun.<br /><br /> Uygulama doğrulaması başarılı olmadı. Devam edilemiyor.<br /><br /> Uygulama dosyaları alınamıyor. Dağıtımdaki dosyalar bozuk. | Dağıtımdaki bildirim dosyalarından biri sözdizimsel olarak geçerli değil veya karşılık gelen dosyayla mutabık kılınabilecek bir karma içeriyor. Bu hata, bir derleme içine gömülü bildirimin bozuk olduğunu da gösterebilir. Dağıtımınızı yeniden oluşturun ve uygulamanızı yeniden derleyin ya da bildirimlerinizde el ile hataları bulup onarın. |
| Uygulama alınamıyor. Kimlik doğrulama hatası.<br /><br /> Uygulama yüklemesi başarılı olmadı. Sunucudaki uygulama dosyaları bulunamıyor. Yardım için uygulama yayımcısına veya yöneticinize başvurun. | Dağıtımdaki bir veya daha fazla dosya, bunlara erişim izniniz olmadığından indirilemiyor. Bunun nedeni, bir Web sunucusu tarafından döndürülen 403 yasaklanmış bir hata olabilir. bu durum, dağıtımınızdaki dosyalardan biri Web sunucusunun korumalı bir dosya olarak kabul eden bir uzantıyla biterse meydana gelebilir. Ayrıca, bir veya daha fazla uygulama dosyasını içeren bir dizin, erişim için bir Kullanıcı adı ve parola gerektirebilir. |
| Uygulama indirilemiyor. Uygulamada gerekli dosyalar eksik. Yardım için uygulama satıcısına veya sistem yöneticinize başvurun. | Uygulama bildiriminde listelenen bir veya daha fazla dosya sunucuda bulunamıyor. Tüm dağıtımın bağımlı dosyalarını karşıya yükleyip yüklemediğinize emin olun ve yeniden deneyin. |
| Uygulama indirmesi başarılı olmadı. Ağ bağlantınızı denetleyin veya sistem yöneticinize veya ağ hizmeti sağlayıcısına başvurun. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sunucuya ağ bağlantısı kurulamıyor. Sunucunun kullanılabilirliğini ve ağınızın durumunu inceleyin. |
| URLDownloadToCacheFile, HRESULT ' ' ile başarısız oldu \<number> . ' ' İndirilmeye çalışılırken bir hata oluştu \<file> . | bir kullanıcı, dağıtım hedef bilgisayarında ınternet explorer gelişmiş güvenlik seçeneğini "güvenli ve güvenli olmayan mod arasında değişiklik yaptıysanız uyar" olarak ayarlandıysa ve yüklenen ClickOnce uygulamanın kurulum URL 'si güvenli olmayan bir siteye (veya tersi) yönlendirilirse, ınternet Explorer uyarısı bunu kestiğinden yükleme başarısız olur.<br /><br /> Bu hatayı çözmek için aşağıdaki görevlerden birini yapabilirsiniz:<br /><br /> -Güvenlik seçeneğini temizleyin.<br />-Kurulum URL 'sinin güvenlik modlarını değiştiren bir şekilde yeniden yönlendirilmediğinden emin olun.<br />-Yeniden yönlendirmeyi tamamen kaldırın ve gerçek kurulum URL 'sini işaret edin. |
| Sabit diske yazılırken bir hata oluştu. Diskte yeterli alan yok olabilir. Yardım için uygulama satıcısına veya sistem yöneticinize başvurun. | Bu, uygulamayı depolamak için yeterli disk alanı olduğunu gösterebilir, ancak uygulama dosyalarını sürücüye kaydetmeye çalışırken daha genel bir g/ç hatası da belirtebilir. |
| Uygulama başlatılamıyor. Diskte yeterli kullanılabilir alan yok. | Sabit disk dolu. Alanı temizleyin ve uygulamayı yeniden çalıştırmayı deneyin. |
| Çok fazla dağıtılan etkinleştirme aynı anda yüklenmeye çalışıyor. | [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aynı anda başlayabilirler farklı uygulama sayısını sınırlar. Bu, yerel hizmette karşı hizmet reddi saldırılarını önlemeye yönelik kötü niyetli saldırılara karşı korunmaya yardımcı olur [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ; aynı uygulamayı art arda başlatmaya çalışan kullanıcılar, hızlı bir şekilde, uygulamanın yalnızca tek bir örneği ile sona acaktır. |
| Kısayollar ağ üzerinden etkinleştirilemez. | Bir uygulamanın kısayolları [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yalnızca yerel sabit diskte başlatılabilir. Uzak bir sunucudaki kısayol dosyasına işaret eden bir URL açılarak başlatılamaz. |
| Uygulama kısmi güvende çevrimiçi çalıştırılamayacak kadar büyük. Yardım için uygulama satıcısına veya sistem yöneticinize başvurun. | Kısmi güvende çalışan bir uygulama, varsayılan olarak 250 MB olan çevrimiçi uygulama kotasının boyutunun yarısından daha büyük olamaz. |

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce dağıtım sorunlarını giderme](../deployment/troubleshooting-clickonce-deployments.md)
- [Visual Studio sorunlarını giderme](/troubleshoot/visualstudio/welcome-visual-studio/)