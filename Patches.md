# Do the following: 
```
# Add makefiles to bengal HAL
cp hardware/qcom-caf/common/os_pickup.mk hardware/qcom-caf/bengal/Android.mk
cp hardware/qcom-caf/common/os_pickup_qssi.bp hardware/qcom-caf/bengal/Android.bp

cd hardware/qcom-caf/common
# Split bengal and kona SOC families
curl -s https://raw.githubusercontent.com/bleedingedgeandroid/patches-pixelos-spes/fourteen-pixelos/hardware/qcom-caf/common/0001-Split-bengal-and-kona-SoC-families.patch -s | git am
cd ../../..

cd vendor/qcom/opensource/interfaces
# Introduce FM HAL
curl -s https://github.com/PixelExperience/vendor_qcom_opensource_interfaces/commit/0a1e8499b11c9c80a58510faa7f63e2d85ab831d.patch | git am
cd ../../../..

rm -rf vendor/qcom/opensource/commonsys/fm device/qcom/vendor-common/memtrack/Android.bp # We already have another thing providing these(fm from device/qcom/vendor-common/commonsys/fm)
```