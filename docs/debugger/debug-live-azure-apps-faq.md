---
title: Anlık görüntü hata ayıklaması hakkında SSS | Microsoft Docs
description: Visual Studio 'daki Snapshot Debugger kullanarak canlı Azure uygulamalarında hata ayıklarken oluşabilecek sık sorulan sorular (SSS) listesini gözden geçirin.
ms.custom: SEO-VS-2020
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9bd8a80f7f6d11587c9f0cd5c6b9bf96e38a0a74
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800499"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Visual Studio 'da anlık görüntü hata ayıklaması için sık sorulan sorular

Snapshot Debugger kullanarak canlı Azure uygulamalarında hata ayıklarken oluşabilecek soruların bir listesi aşağıda verilmiştir.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Anlık görüntü alma performans maliyeti nedir?

Snapshot Debugger uygulamanızın bir anlık görüntüsünü yakaladığında, uygulamanın sürecini çatallandırın ve ele geçirilen kopyayı askıya alır. Bir anlık görüntüde hata ayıkladığınızda, işlemin yürütülen kopyasına göre hata ayıklaması yapılır. Bu işlem yalnızca 10-20 milisaniye sürer ancak uygulamanın tam yığınını kopyalamaz. Bunun yerine, yalnızca sayfa tablosunu kopyalar ve yazma üzerine kopyalamak için sayfaları ayarlar. Uygulamanızın yığındaki bazı nesneler değiştiğinde ilgili sayfaları kopyalanır. Bu, her anlık görüntünün küçük bir bellek içi maliyeti vardır (çoğu uygulama için yüzlerce kilobayt sırasıyla).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Ölçeği genişletilmiş bir Azure App Service (uygulamamın birden çok örneği) varsa ne olur?

Uygulamanızın birden çok örneğine sahip olduğunuzda, anlık görüntü noktaları her tek örneğe uygulanır. Yalnızca belirtilen koşullara uyan ilk anlık görüntü noktası bir anlık görüntü oluşturur. Birden çok anlık görüntü noktanız varsa, sonraki anlık görüntüler ilk anlık görüntüyü oluşturan örnekten gelir. Çıkış penceresine gönderilen günlüğe kaydetme noktaları 'ler yalnızca bir örnekten gelen iletileri gösterir, ancak uygulama günlüklerine gönderilen günlüğe kaydetme noktaları her örnekten ileti gönderir.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Snapshot Debugger sembolleri nasıl yükleyebilir?

Snapshot Debugger, uygulamanız için yerel ya da Azure App Service dağıtılan eşleşen simgelere sahip olmanızı gerektirir. (Embedded pdb 'leri Şu anda desteklenmiyor.) Snapshot Debugger, Azure App Service sembolleri otomatik olarak indirir. Visual Studio 2017 sürüm 15,2 ' den başlayarak, Azure App Service dağıtım, uygulamanızın sembollerini de dağıtır.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Uygulamam Snapshot Debugger derlemelerine karşı çalışıyor mu?

Evet - Snapshot Debugger derlemelere karşı çalışması amaçlanan bir uygulamadır. Bir işleve ek bileşen yerleştirilsin, işlev bir hata ayıklama sürümüne geri yeniden kodlanabilir ve bu da hata ayıklanabilir hale döner. Bu Snapshot Debugger, işlevleri yayın derlemesi sürümüne döndürür.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Logpoint'ler üretim uygulamamda yan etkilere neden olabilir mi?

Hayır - Uygulamanıza ekley istediğiniz günlük iletileri sanal olarak değerlendirilir. Bunlar uygulamanıza herhangi bir yan etkiye neden olabilir. Ancak, bazı yerel özelliklere günlük noktalarıyla erişilemiyor olabilir.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Sunucum Snapshot Debugger sunucum çalışıyor mu?

Evet, anlık görüntü hata ayıklaması yük altındaki sunucular için kullanılabilir. Bu Snapshot Debugger, sunucunuzda düşük miktarda boş bellek bulunduğu durumlarda anlık görüntüleri kısıtlamaz ve yakalamaz.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Nasıl yaparım? kaldırabilirsiniz Snapshot Debugger?

Aşağıdaki adımları Snapshot Debugger site uzantınızı App Service site uzantısını kaldırabilirsiniz:

1. App Service'daki Bulut Gezgini'Visual Studio veya Azure portal.
1. Uygulamanıza App Service kudu sitesine (yani, uygulama hizmetinize) gidin.**scm**.azurewebsites.net) ve **Site uzantıları'ne gidin.**
1. Site uzantısını kaldırmak Snapshot Debugger X'e tıklayın.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Bağlantı noktaları neden bir oturum Snapshot Debugger açıldı?

Snapshot Debugger azure'da alınan anlık görüntülerde hata ayıklamak için bir bağlantı noktası kümesi açmanız gerektiğinde, bunlar uzaktan hata ayıklama için gereken bağlantı noktalarıyla aynıdır. [Bağlantı noktalarının listesini burada bulabilirsiniz.](../debugger/remote-debugger-port-assignments.md)

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Nasıl yaparım? Hata Ayıklayıcısı uzantısını devre dışı bırakmak mı?

Uygulama Hizmetleri için:
1. App Service için Azure portal uzaktan hata ayıklayıcı uzantısını devre dışı bırakın.
2. Uygulama *ayarlarını* > uygulama hizmeti kaynak dikey penceresini > Azure Portal
3. *Hata ayıklama* bölümüne gidin ve *Uzaktan hata ayıklama* için *kapalı* düğmesine tıklayın.

AKS için:
1. [Docker görüntülerinde Visual Studio Snapshot Debugger](https://github.com/Microsoft/vssnapshotdebugger-docker)karşılık gelen bölümleri kaldırmak Için Dockerfile dosyanızı güncelleştirin.
2. Değiştirilen Docker görüntüsünü yeniden derleyin ve yeniden dağıtın.

Sanal makine/sanal makine ölçek kümeleri için uzaktan hata ayıklayıcı uzantısı, sertifikalar, Anahtar kasaları ve gelen NAT havuzlarını aşağıdaki gibi kaldırın:

1. Uzaktan hata ayıklayıcı uzantısını kaldır

   Sanal makineler ve sanal makine ölçek kümeleri için uzak hata ayıklayıcıyı devre dışı bırakmak için çeşitli yollar vardır:

      - Bulut Gezgini aracılığıyla uzaktan hata ayıklayıcıyı devre dışı bırakma

         - Cloud Explorer > hata ayıklamayı devre dışı bırak (bulut Gezgini 'nde sanal makine ölçek kümesi için hata ayıklamayı devre dışı bırakma yok) >.

      - Uzaktan hata ayıklayıcıyı PowerShell betikleri/cmdlet 'Leriyle devre dışı bırakma

         Sanal makine için:

         ```powershell
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger
         ```

         Sanal Makine Ölçek Kümeleri için:

         ```powershell
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension
         ```

      - Azure portal aracılığıyla uzaktan hata ayıklayıcıyı devre dışı bırakın
         - Azure portal sanal makineniz/sanal makine ölçek kümeleri kaynak dikey penceresi > uzantıları >
         - Microsoft. VisualStudio. Azure. RemoteDebug. VSRemoteDebugger uzantısını kaldır

         > [!NOTE]
         > Sanal Makine Ölçek Kümeleri-Portal DebuggerListener bağlantı noktalarının kaldırılmasına izin vermez. Azure PowerShell kullanmanız gerekir. Ayrıntılar için aşağıya bakın.

2. Sertifikaları ve Azure KeyVault'ı kaldırma

   Sanal makine veya sanal makine ölçek kümeleri için Uzaktan Hata Ayıklayıcı uzantısını yüklerken, Azure Sanal Makine/sanal makine ölçek kümeleri kaynaklarıyla Visual Studio istemcinin kimliğini doğrulamak için hem istemci hem de sunucu sertifikaları oluşturulur.

   - İstemci Sertifikası

      Bu sertifika, Cert:/CurrentUser/My/ içinde bulunan otomatik olarak imzalanan bir sertifikadır

      ```
      Thumbprint                                Subject
      ----------                                -------

      1234123412341234123412341234123412341234  CN=ResourceName
      ```

      Bu sertifikayı makineden kaldırmanın bir yolu PowerShell aracılığıyla kaldırmaktır

      ```powershell
      $ResourceName = 'ResourceName' # from above
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item
      ```

   - Sunucu Sertifikası
      - İlgili sunucu sertifikası parmak izi, Azure KeyVault'a gizli anahtar olarak dağıtılır. Visual Studio makine veya sanal makine ölçek kümeleri kaynağına karşılık gelen bölgede MSVSAZ* ön ekli bir KeyVault bulmaya veya oluşturmaya çalışacak. Bu nedenle, bu bölgeye dağıtılan tüm sanal makine veya sanal makine ölçek kümeleri kaynakları aynı KeyVault'ları paylaşır.
      - Sunucu sertifikası parmak izi gizli anahtarını silmek için Azure portal gidin ve kaynağınızı barındıran bölgede MSVSAZ* KeyVault'unu bulun. Etiketlenmiş olması gereken gizli adı silin `remotedebugcert<<ResourceName>>`
      - Ayrıca PowerShell aracılığıyla kaynağından sunucu gizli ını da silmeniz gerekir.

      Sanal makineler için:

      ```powershell
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVM -ResourceGroupName $rgName -VM $vm
      ```

      Sanal makine ölçek kümeleri için:

      ```powershell
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss
      ```

3. Tüm DebuggerListener Gelen NAT havuzlarını kaldırma (yalnızca sanal makine ölçek kümesi)

   Uzaktan Hata Ayıklayıcı, ölçek kümenizin yük dengeleyiciye uygulanan DebuggerListener bağlı NAT havuzlarını tanıtıyor.

   ```powershell
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null

   if ($LoadBalancerName)
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null
      Set-AzLoadBalancer -LoadBalancer $lb
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>Nasıl yaparım? devre dışı Snapshot Debugger?

Daha App Service:
1. Kendi Snapshot Debugger için Azure portal aracılığıyla App Service.
2. Uygulama *ayarlarını* > uygulama hizmeti kaynak dikey penceresini > Azure Portal
3. Azure portal aşağıdaki uygulama ayarlarını silin ve değişikliklerinizi kaydedin.
   - INSTRUMENTATIONENGINE_EXTENSION_VERSION
   - SNAPSHOTDEBUGGER_EXTENSION_VERSION

   > [!WARNING]
   > Uygulama ayarlarında yapılan değişiklikler, uygulamanın yeniden başlatılmasını başlatır. Uygulama ayarları hakkında daha fazla bilgi için, [Azure portal App Service uygulama yapılandırma](/azure/app-service/web-sites-configure)konusuna bakın.

AKS için:
1. [Docker görüntülerinde Visual Studio Snapshot Debugger](https://github.com/Microsoft/vssnapshotdebugger-docker)karşılık gelen bölümleri kaldırmak Için Dockerfile dosyanızı güncelleştirin.
2. Değiştirilen Docker görüntüsünü yeniden derleyin ve yeniden dağıtın.

Sanal makine/sanal makine ölçek kümeleri için:

Snapshot Debugger devre dışı bırakmak için birkaç yol vardır:
- Bulut Gezgini > sanal makineniz/sanal makine ölçek kümesi kaynağınız > tanılamayı devre dışı bırak

- Azure portal > sanal makineniz/sanal makine ölçek kümesi kaynak dikey penceresi > uzantıları > Microsoft. Insights. VMDiagnosticsSettings uzantısını kaldır

- [Az PowerShell](/powershell/azure/overview) 'Den PowerShell cmdlet 'leri

   Sanal makine:

   ```powershell
      Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

   Sanal Makine Ölçek Kümeleri:

   ```powershell
      $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
      Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Hata Ayıklama](../debugger/index.yml)
- [Snapshot Debugger kullanarak canlı ASP.NET uygulamalarında hata ayıklama](../debugger/debug-live-azure-applications.md)
- [Snapshot Debugger kullanarak canlı ASP.NET Azure sanal makine ölçek kümelerinde hata ayıkla](../debugger/debug-live-azure-virtual-machines.md)
- [Snapshot Debugger kullanarak canlı ASP.NET Azure Kubernetes hatalarını ayıklama](../debugger/debug-live-azure-kubernetes.md)
- [Anlık görüntü hata ayıklaması için sorun giderme ve bilinen sorunlar](../debugger/debug-live-azure-apps-troubleshooting.md)
