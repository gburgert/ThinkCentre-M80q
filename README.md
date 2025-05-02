# ThinkCentre-M80q Ventura  
05/05/2023  
Model 316C  
  
## Levantar a conf do sistema  
https://github.com/KernelWanderers/OCSysInfo/releases  
```
Chipset - ID0687
─ CPU
  └── Intel(R) Core(TM) i7-10700T CPU @ 2.00GHz COMET LAKE
      ├── Cores: 8
      ├── Threads: 16
      ├── SSE: SSE4.2
      └── SSSE3: Supported

─ Motherboard
  ├── Model: 316C
  └── Manufacturer: LENOVO

─ GPU
  ├── Intel(R) UHD Graphics 630
  │   ├── Device ID: 0x9BC5
  │   ├── Vendor: 0x8086
  │   ├── PCI Path: PciRoot(0x0)/Pci(0x2,0x0)
  │   └── ACPI Path: \_SB.PCI0.GFX0
  └── Microsoft Remote Display Adapter

─ Memory
  ├── HEMA81GS6DJR8N-XN (Part-Number)
  │   ├── Type: DDR4
  │   ├── Slot
  │   │   ├── Bank: BANK 0
  │   │   └── Channel: ChannelA-DIMM0
  │   ├── Frequency (MHz): 2933 MHz
  │   ├── Manufacturer: 0B5E
  │   └── Capacity: 8192MB
  └── HEMA81GS6DJR8N-XN (Part-Number)
      ├── Type: DDR4
      ├── Slot
      │   ├── Bank: BANK 2
      │   └── Channel: ChannelB-DIMM0
      ├── Frequency (MHz): 2933 MHz
      ├── Manufacturer: 0B5E
      └── Capacity: 8192MB

─ Network
  ├── Comet Lake PCH CNVi WiFi
  │   ├── Device ID: 0x06F0
  │   ├── Vendor: 0x8086
  │   ├── PCI Path: PciRoot(0x0)/Pci(0x14,0x3)
  │   └── ACPI Path: \_SB.PCI0.CNVW
  └── Ethernet Connection (11) I219-LM
      ├── Device ID: 0x0D4C
      ├── Vendor: 0x8086
      ├── PCI Path: PciRoot(0x0)/Pci(0x1f,0x6)
      └── ACPI Path: \_SB.PCI0.GLAN

─ Audio
  ├── Intel(R) Display Audio
  │   ├── Device ID: 0x280B
  │   └── Vendor: 0x8086
  └── Realtek ALC235
      ├── Device ID: 0x0235
      └── Vendor: 0x10EC

─ Input
  ├── USB Input Device (USB)
  │   ├── Product ID: 0x6099
  │   └── Vendor ID: 0x17EF
  └── USB Input Device (USB)
      ├── Product ID: 0x608D
      └── Vendor ID: 0x17EF

─ Storage
  ├── ST500LM012 HN-M500MBB
  │   ├── Type: Hard Disk Drive (HDD)
  │   ├── Connector: Serial ATA (SATA)
  │   └── Location: Internal
  └── UMIS RPETJ512MGE2QDQ
      ├── Type: NVMe
      ├── Connector: PCI Express
      └── Location: Internal
```
  
## Ferramentas Windows  
Ferramentas que precisa pra fazer um boot funcional no windows.  
\
**Instalar choco**  
Abrir powershell admin  
```
Get-ExecutionPolicy  
--> Restricted  
Set-ExecutionPolicy AllSigned  
Get-ExecutionPolicy  
--> ByPass  
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))  
choco  
-->v2.3.0  
```
\
**Instalar python3**  
```
choco install python  
```
\
**Instalar git**  
Abrir powershell com permissão de admin  
```
choco install git  
```
Precisa fechar e abrir de novo o powershell pro git entrar no path  
\
**Baixar propertree**  
https://github.com/corpnewt/ProperTree  
```
git clone https://github.com/corpnewt/ProperTree  
ProperTree\Scripts\AssociatePlistFiles.bat  
```
\
**Gerador de serial. Tentei seguir sem gerar o serial, nem boota**  
```
git clone https://github.com/corpnewt/GenSMBIOS  
```
\
**Vai precisar do Explorer++ no Windows**  
```
choco install explorerplusplus  
```
\
**SDDTTime - vários SSDTs**  
https://github.com/corpnewt/SSDTTime  
```  
git clone https://github.com/corpnewt/SSDTTime.git  
```
\
**Instala o usb tool do Windows**  
https://github.com/USBToolBox/tool  
  
**Instala dd e 7zip. Precisa pro gibMacOS**
```
choco install 7zip
choco install dd
```

## Ferramentas MacOS  
Ferramentas para o refinamento do sistema.  
\
**Mountefi**  
https://github.com/corpnewt/MountEFI  
Para atualizar o config.plist pelo mac.  
```
git clone https://github.com/corpnewt/MountEFI  
cd MountEFI  
chmod +x MountEFI.command  
```
\
**IORegistry**  
https://github.com/khronokernel/IORegistryClone/blob/master/ioreg-302.zip  
Ajuda num monte de coisa. Usei pra verificar se precisa ou não do SSDT-PLUG.  
\
**Hakintool**  
https://github.com/benbaker76/Hackintool/  
Como ele mesmo diz, canivete suíço do hackintosh. Se não usar agora, vai usar em algum momento.  
  
**MaciASL**  
https://github.com/acidanthera/MaciASL  
Esse cara vai abrir os aml (tabela ACPI) que o SSDTTime vai fazer o dump. 
  
**Homebrew**  
https://brew.sh/  
Precisa pra tudo. O apt-get do mac.
```  
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"  
```
\
**Propertree no mac**  
Fica com tela preta. Pra resolver precisa instalar tk mais novo.  
```
python3 --version 
--> Python 3.9.6 (versão nativa). Vou atualizar com o brew.
brew install python
--> Python has been installed as
--> /usr/local/bin/python3
brew install python-tk
--> abrir um terminal novo
python3 --version
--> Python 3.12.5
cd hackintosh/Propertree-master/Scripts
python3 buildapp-select.py --> escolher tk 8.6
--> Saved to: hackintosh/ProperTree/ProperTree.app
```
Copia o ProperTree.app para o /Applications  
  
## Criando o pendrive no Mac usando gibMacOS  
Baixar  https://github.com/corpnewt/gibMacOS/archive/master.zip  
```
C:\Users\gb\hackintosh\gibMacOS-master\gibMacOS.bat  
```
Não tem mais recovery do big sur pra cima  
-> opção 14. macOS Ventura 13.7.2 (22H313)   
  
Executar makeinstall.bat como admin  
-> opção 1O para formatar com Opencore  
-> caminho "C:\tmp\hackintosh\gibMacOS-master\macOS Downloads\publicrelease\072-36728 - 13.7.2 macOS Ventura (22H313)"  

OBS: depois de algumas tentativas parou de funcionar. Troquei de usb aí voltou.  
  
```
  #######################################################
 #                Installing OpenCore                  #
#######################################################

Gathering info...
 - Got OpenCore-1.0.4-RELEASE.zip
Downloading...
Downloaded 2.62 MB of 2.62 MB (100.00%)
Extracting OpenCore-1.0.4-RELEASE.zip...
Gathering DUET boot files...
 - boot
 - boot0
 - boot1f32
Copying EFI folder to E:/EFI...
Copying boot to E:/boot...
Updating the MBR with boot0...
Updating the PBR with boot1f32...
Cleaning up...

Done.

Press [enter] to return to the main menu...
quit
```

## Preparando o EFI  
https://dortania.github.io/OpenCore-Install-Guide/installer-guide/opencore-efi.html  
Essa parte é no Windows, na máquina que vai receber o MacOS.  

Copiar OpenCore-1.0.4-DEBUG\X64\EFI. Daqui pra frente usa a cópia dessa pasta. 
Arquivos importantes:  

    EFI\OC\OpenCore.efi  
    EFI\OC\config.plist  
  
### Drivers  
**Drivers Opencore**  
--> em EFI\OC\Drivers deixa ResetNvramEntry.efi, OpenRuntime.efi  
  
**Driver Hfsplus**  
https://github.com/acidanthera/OcBinaryData/blob/master/Drivers/HfsPlus.efi  
--> pega HfsPlus.efi e coloca no EFI\OC\Drivers  
  
### Tools  
**Tools opencore**  
--> em EFI\OC\Tools fica com OpenShell.efi, MmapDump.efi, ResetSystem.efi  
  
### Kexts  
**kexts lilo**  
https://github.com/acidanthera/Lilu/releases  
--> fica com lilo.kext  
  
**kexts virtualsmc**  
https://github.com/acidanthera/VirtualSMC/releases  
--> fica com SMCProcessor.kext, SMCSuperIO.kext, VirtualSMC.kext  
  
**kexts WhateverGreen**  
https://github.com/acidanthera/WhateverGreen/releases  
--> fica com WhateverGreen.kext  
  
**kexts Audio**  
https://github.com/acidanthera/AppleALC/releases  
--> fica com AppleALC.kext  
  
**Rede Intel**   
https://github.com/acidanthera/IntelMausi/releases  
--> fica com IntelMausi.kext (não sei pra que serve o IntelSnowMausi)  
  
**kexts usb**   
https://github.com/USBToolBox/kext  
--> fica com USBToolBox.kext, UTBDefault.kext. Vou fazer o kext no windows  
  
**kext nvme**  
https://github.com/acidanthera/NVMeFix/releases  
--> fica com NVMeFix.kext  
  
**kext sata unsupported**  
https://github.com/dortania/OpenCore-Install-Guide/blob/master/extra-files/CtlnaAHCIPort.kext.zip
--> CtlnaAHCIPort.kext
  
**kexts bluetooth**  
https://openintelwireless.github.io/IntelBluetoothFirmware/  
--> IntelBTPatcher.kext  
--> IntelBluetoothFirmware.kext  
--> remove IntelBluetoothInjector.kext  

https://github.com/acidanthera/BrcmPatchRAM  
--> BlueToolFixup.kext  
  
**kexts wifi**  
https://github.com/OpenIntelWireless/itlwm/releases/tag/v2.3.0  
--> AirportItlwm.kext  

### ACPI para Cometlake 
https://dortania.github.io/Getting-Started-With-ACPI/ssdt-methods/ssdt-prebuilt.html#desktop-comet-lake  
  
https://dortania.github.io/Getting-Started-With-ACPI/Universal/plug.html  
https://dortania.github.io/Getting-Started-With-ACPI/Universal/ec-fix.html  
https://dortania.github.io/Getting-Started-With-ACPI/Universal/awac.html  
https://dortania.github.io/Getting-Started-With-ACPI/Universal/rhub.html  
   
## Montar o config.plist  
```
cd hackintosh
copy .\OpenCore-1.0.4-DEBUG\Docs\Sample.plist .\EFI\OC\config.plist
```

Abrir propertree, abrir config.plist  
-> File -> OC Clean Snapshot  
Apontar para /EFI/OC que está sendo montado
https://dortania.github.io/OpenCore-Install-Guide/config.plist/comet-lake.html#starting-point  

    Root->Booter->Quirks
      DevirtualiseMmio:True
      EnableWriteUnprotector:False
      ProtectUefiServices:True
      RebuildAppleMemoryMap:True
      ResizeAppleGpuBars:-1
      SetupVirtualMap:False
      SyncRuntimePermissions:True 
  
Root->DeviceProperties  
Verificar https://github.com/acidanthera/WhateverGreen/blob/master/Manual/FAQ.IntelHD.en.md#intel-uhd-graphics-610-655-coffee-lake-and-comet-lake-processors  
device-id 0x9BC5 -> está na lista de suportado. Não precisa de framebuffer.  
Vou deixar vazio, mas se precisar está aqui  
AAPL,ig-platform-id 	data 00009B3E 	Alternative to 07009B3E if it doesn't work  

    Root->Kernel->Quirks  
      AppleXcpmCfgLock 	True 	Not needed if CFG-Lock is disabled in the BIOS  
      DisableIoMapper 	False 	Not needed if VT-D is disabled in the BIOS  
      LapicKernelPanic: False  
      PanicNoKextDump: True  
      PowerTimeoutKernelPanic: True  
      XhciPortLimit: False
.  
  
    Root->Misc
      Boot->HideAuxiliary:True
      Debug
        AppleDebug 	YES
        ApplePanic 	YES
        DisableWatchDog 	YES
        Target 	67
        Sysreport True
      Security
        AllowSetDefault: YES 	
        BlacklistAppleUpdate: YES 	
        ScanPolicy: 0 	
        SecureBootModel: Default
        Vault: Optional
  
Teclado https://github.com/acidanthera/OpenCorePkg/blob/master/Utilities/AppleKeyboardLayouts/AppleKeyboardLayouts.txt  
[128] pt_BR - Brazilian-ABNT2 (lingua:teclado)  

    Root->NVRam
      boot-args: debug=0x100 alcid=3
      prev-lang:kbd String en-US:128

Agora roda o gensmbios
```
cd GenSMBIOS
GenSMBIOS.bat
```
-> opção 3, iMac20,1
```
  #######################################################
 #                iMac20,1 SMBIOS Info                 #
#######################################################

Type:         iMac20,1
Serial:       C02HDDZ6PN5T
Board Serial: C022091024NPHC1JC
SmUUID:       221F21B1-A5A8-4BCF-AB06-EBE8DA89A9A4
Apple ROM:    00CDFE585039

Type:         iMac20,1
Serial:       C02DT0JUPN5T
Board Serial: C02050300QXPHC11M
SmUUID:       09189825-6B70-4D97-B693-703B4A98D474
Apple ROM:    F0CBA1BF2801

Type:         iMac20,1
Serial:       C02HNEY0PN5T
Board Serial: C02218108J9PHC1JC
SmUUID:       8690E612-0A67-40C1-A0DE-28B5918D13A8
Apple ROM:    4C3275071CD5
```
Testa aqui https://checkcoverage.apple.com/  
Precisa dar inválido. Se retornar produto gera outro.  
Deu pro C02HCDZ6PN5T
```
MLB C022091024NPHC1JC
ROM 00CDFE585039
SystemProductName iMac20,1
SystemSerialNumber C02HDDZ6PN5T
SystemUUID 221F21B1-A5A8-4BCF-AB06-EBE8DA89A9A4
```

## Intel BIOS settings  
### Disable  
    OK Fast Boot  
    OK Secure Boot  
    xx Serial/COM Port  
    xx Parallel Port  
    OK VT-d
    xx Compatibility Support Module (CSM) (Must be off in most cases, GPU errors/stalls like gIO are common when this option is enabled)  
    xx Thunderbolt  
    OK Intel SGX  
    xx Intel Platform Trust  
    xx CFG Lock (MSR 0xE2 write protection)(This must be off, if you can't find the option then enable AppleXcpmCfgLock under Kernel -> Quirks. Your hack will not boot with CFG-Lock enabled)  
  
### Enable  
    OK VT-x  
    xx Above 4G Decoding  
        2020+ BIOS Notes: When enabling Above4G, Resizable BAR Support may become an available on some Z490 and newer motherboards. Please ensure that Booter -> Quirks -> ResizeAppleGpuBars is set to 0 if this is enabled.  
    OK Hyper-Threading  
    xx Execute Disable Bit  
    xx EHCI/XHCI Hand-off  
    xx OS type: Windows 8.1/10 UEFI Mode (some motherboards may require "Other OS" instead)  
    OK DVMT Pre-Allocated(iGPU Memory): 64MB or higher  
    OK SATA Mode: AHCI  
  
## PostInstall  
  
### Completar o mapeamento de USB  
https://github.com/USBToolBox/kext  

    Add USBToolBox.kext and UTBDefault.kext to your EFI/OC/Kexts folder, and make sure to update your config.plist.
    Install macOS.
    Map your ports with the USBToolBox tool.
    Remove UTBDefault.kext and add your newly created UTBMap.kext (or whatever your USB map is called) to EFI/OC/Kexts.
    Reboot and you should have a USB mapped system!

Baixar https://github.com/USBToolBox/tool pra mac    
Rodar no macos  
```
--> D para discovery  
```
Plugar pendrives usb2 e usb3 em todas as portas  
  
MAPA  

    2 - Frente A SS10  
    4 - Frente C SS  
    5 - Atrás ao lado do conector de rede A SS10  
    6 - Atrás SS10  
    7 - Atrás teclado A SS  
    8 - Atrás mouse A SS  
    14 - Internal  
```
--> T:2,5,6,7,8:3  
--> T:14:255  
--> T:4:9  
```
Escolhi o type c com switch, tipo 9  
```
--> k para gerar o UTBMap.kext  
--> b, b, q  
```
Copiar o UTBMap.kext no EFI/Kexts e adicionar no config.plist. Em root->kernel->add encontrar o UTBDefault.kext e colocar em false.  
  
### Mapeamento de porta HDMI - Intel(R) UHD Graphics 630  
https://dortania.github.io/OpenCore-Post-Install/gpu-patching/intel-patching/busid.html  
UHD630, framebuffer 0x3E9B0007 --> AAPL,ig-platform-id Data  07009B3E  
  
Entradas para esse framebuffer  
https://github.com/acidanthera/WhateverGreen/blob/master/Manual/FAQ.IntelHD.en.md  
```
[1] busId: 0x05, pipe: 9, type: 0x00000400, flags: 0x000003C7 - ConnectorDP
[2] busId: 0x04, pipe: 10, type: 0x00000400, flags: 0x000003C7 - ConnectorDP
[3] busId: 0x06, pipe: 8, type: 0x00000400, flags: 0x000003C7 - ConnectorDP
01050900 00040000 C7030000  --> con0
02040A00 00040000 C7030000  --> con1
03060800 00040000 C7030000  --> con2
```
--> a saída de vídeo hdmi é a 0 ou 3, porque deu tela preta se bootar com a hdmi  
--> chuto que essa saída é a 3. Vou mapear ela na 0  

Vai isso pro config.plist:  
```
Root->DeviceProperties->Add  
    PciRoot(0x0)/Pci(0x2,0x0)  
        AAPL,ig-platform-id Data  07009B3E  
        device-id Data 3E9B0007  
        framebuffer-patch-enable Data 01000000  
        framebuffer-con2-enable Data 01000000  
        framebuffer-con2-alldata Data 03060900 00080000 C7030000  
```

O que não funcionou  
```
con-0 03060900
con-2 03060900
con-2 03060900 sem device-id
device-id 00009B3E
```
Não rolou nada disso. Vou para o método força bruta (Mapping without macOS)  
```
framebuffer-patch-enable | Data | `01000000`
framebuffer-con0-enable  | Data | `01000000`
framebuffer-con1-enable  | Data | `01000000`
framebuffer-con2-enable  | Data | `01000000`
framebuffer-con0-alldata | Data | `01010900 00080000 C7030000`
framebuffer-con1-alldata | Data | `02000A00 00040000 C7030000`
framebuffer-con2-alldata | Data | `03000800 00040000 C7030000`
```
Também nao tá indo...  

===> Receita vencedora <===  
https://www.tonymacx86.com/threads/guide-general-framebuffer-patching-guide-hdmi-black-screen-problem.269149/  
--> Hackintool  
Verificar menu Framebuffer >= macOS  10.14  
Nos ícones, clicar em patch->connectors  
1 0x05 9 DP 3C7 <-- Display port em uso (vermelho)  
2 0x04 10 DP 3C7 <-- VGA  
3 0x06 8 DP 3C7 <-- só pode ser o HDMI  
Sugestão dele, trocar o BusID da porta 2 com a 3 e arrumar o Type para HDMI  
  
Edit config.plist
```
Root->DeviceProperties->Add
    PciRoot(0x0)/Pci(0x2,0x0)
        framebuffer-patch-enable | Data | `01000000`
        framebuffer-con0-enable  | Data | `01000000`
        framebuffer-con1-enable  | Data | `01000000`
        framebuffer-con2-enable  | Data | `01000000`
        framebuffer-con0-alldata | Data | `01050900 00040000 C7030000`
        framebuffer-con1-alldata | Data | `02060A00 00040000 C7030000`
        framebuffer-con2-alldata | Data | `03040800 00040000 C7030000`

```
\
**Arrumar o som**  
config.plist: Root->nvram->add->7C..82->boot-args  
--> adicionar alcid=16  
  
**Resolver o problema do 2o monitor que não liga**
https://www.reddit.com/r/hackintosh/comments/g1194b/catalina_no_hdmi_signal_after_wake_from_sleep_oc/  
config.plist: Root->NVRAM->add->7c..82->boot-args  
--> adicionar igfxonln=1 igfxonlnfbs=0x02  
  
**Smbus support - temperaturas e ventoinhas**  
https://dortania.github.io/Getting-Started-With-ACPI/Universal/smbus-methods/manual.html#hackintool  
--> roda hackingtool, tab PCIe, procura subclass SMBus, pega IORegName
/PCI0@0/SBUS@1F,4 ==> PCI0.SBUS (tira os arrobas)  
--> edição, baixar o sample https://github.com/acidanthera/OpenCorePkg/tree/master/Docs/AcpiSamples/Source/SSDT-SBUS-MCHC.dsl  
```
External (_SB_.PCI0, DeviceObj) <- Rename this
External (_SB_.PCI0.SBUS.BUS0, DeviceObj) <- Rename this

Scope (_SB.PCI0) <- Rename this
{
    Device (MCHC)
    {
        Name (_ADR, Zero)  // _ADR: Address
    }
}

Device (_SB.PCI0.SBUS.BUS0) <- Rename this
```  
Opa! O nome já bate com a tabela. Não precisa desse patch.  
  
## Polimentos  
**Pin bluetooth to menu bar**  
https://www.iphonetricks.org/add-bluetooth-icon-to-menu-bar-macos-ventura/  
--> engrenagem -> control center -> bluetooth -> show in menu bar  
  
**Disable auto-capitalization**  
Apple icon -> System Settings -> Keyboard  
Text Input -> edit  
    Click to deselect the box next to Capitalize words automatically.  


## Softwares Finais
  
**Filezilla**  
https://filezilla-project.org/  
  
**Intel Power Gadget**  
https://www.intel.com/content/www/us/en/developer/articles/tool/power-gadget.html  
```
brew install --cask intel-power-gadget  
```
**Libre Office**  
https://pt-br.libreoffice.org/baixe-ja/libreoffice-novo/  
```
brew install --cask libreoffice
```
**Teams**  
https://www.microsoft.com/pt-br/microsoft-teams/download-app#for-desktop1  
```
brew install --cask microsoft-teams
```
**Whatsapp**  
```
brew install --cask whatsapp
```
**Citrix Workspace**  
https://www.citrix.com/downloads/workspace-app/mac/workspace-app-for-mac-latest.html  
```
brew install --cask citrix-workspace
```
**Speedtest Ookla**  
https://www.speedtest.net/apps/mac  

**SMCfancontrol**  
```
brew install --cask smcfancontrol
```
**Monitor control para controle de brilho**  
https://github.com/MonitorControl/MonitorControl  
```
brew install MonitorControl
```
**Remote Desktop**  
```
brew install --cask microsoft-remote-desktop
```
**Sequel Ace**  
```
brew install --cask sequel-ace
```
**Openvpn connect**  
```
brew install --cask openvpn-connect
```
**Apache Directory Studio**  
```
brew install --cask apache-directory-studio
```
**precisa do java**
```
brew install --cask temurin
```
**dbeaver**  
```
brew install --cask dbeaver-community
```
**cloudmonkey**  
https://github.com/apache/cloudstack-cloudmonkey/releases  
```
brew install wget
mkdir tmp; cd tmp
wget https://github.com/apache/cloudstack-cloudmonkey/releases/download/6.4.0/cmk.darwin.x86-64
chmod +x cmk.darwin.x86-64
mv cmk.darwin.x86-64 /usr/local/bin/cmk
```
