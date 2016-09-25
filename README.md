# XUPV5-LX110T's config for Xilinx EDK 

[XUPV5-LX110T](http://www.xilinx.com/univ/xupv5-lx110t.htm) is a development board produced in association with Xilinx University Program. It can be seen as a [ML505](http://www.xilinx.com/products/boards/ml505/docs.htm) but hosts a Virtex-5 XC5VLX110T device ([http://www.xilinx.com/univ/xupv5-lx110T-manual.htm](http://www.xilinx.com/univ/xupv5-lx110T-manual.htm)).

For some reason, the Base System Builder in EDK doesn’t support the XUPV5-LX110T board. Moreover, because the board configuration of ML505 contains certain location constraints that are optimal for the Virtex-5 XC5VLX50T but not for the XC5VLX110T, during building bitstream for XUPV5-LX110T you might receive some error like this if you simply use the board configuration of ML505 in EDK by only changing the target device:

> ERROR: Place:713 - IOB component "fpga_0_DDR2_SDRAM_DDR2_DQ_pin<13>" and IODELAY
>  component
>  "DDR2_SDRAM/DDR2_SDRAM/mpmc_core_0/gen_v5_ddr2_phy.mpmc_phy_if_0/u_phy_io_0/g
>  en_dq[13].u_iob_dq/u_idelay_dq" must be placed adjacent to each other into
>  the same I/O tile in order to route net
>  "DDR2_SDRAM/DDR2_SDRAM/mpmc_core_0/gen_v5_ddr2_phy.mpmc_phy_if_0/u_phy_io_0/g
>  en_dq[13].u_iob_dq/dq_in". The following issue has been detected:
>  Some of the logic associated with this structure is locked. This should cause
>  the rest of the logic to be locked.A problem was found at site IODELAY_X0Y56
>  where we must place IODELAY
>  DDR2_SDRAM/DDR2_SDRAM/mpmc_core_0/gen_v5_ddr2_phy.mpmc_phy_if_0/u_phy_io_0/ge
>  n_dq[13].u_iob_dq/u_idelay_dq in order to satisfy the relative placement
>  requirements of this logic.  IODELAY
>  DDR2_SDRAM/DDR2_SDRAM/mpmc_core_0/gen_v5_ddr2_phy.mpmc_phy_if_0/u_phy_io_0/ge
>  n_dqs[0].u_iob_dqs/u_iodelay_dq_ce appears to already be placed there which
>  makes this design unplaceable. 
> ERROR: Pack:1654 - The timing-driven placement phase encountered an error.
> ERROR: Xflow - Program map returned error code 2. Aborting flow execution...
> make: *** [__xps/system_routed] Error 1

Thanks to [Jeff Johnson](http://www.fpgadeveloper.com/author/Jeff) and works he has done ([http://www.fpgadeveloper.com/2011/06/how-to-convert-an-ml505-edk-project-for-the-xupv5.html](http://www.fpgadeveloper.com/2011/06/how-to-convert-an-ml505-edk-project-for-the-xupv5.html)), the EDK now works fine with XUPV5-LX110T. The XUPV5-LX110T config file here is derived from ML505 with the constraints modification made by Jeff Johnson. After installation you can directly select XUPV5-LX110T as you target board without any modification of system.ucf.  

## Installation
1. Close the Base System Builder
2. Copy the whole folder "Xilinx_XUPV5_LX110T" to "**YOUR_ISE_PATH**\\**YOUR_ISE_VERSION**\\ISE_DS\\EDK\\board\Xilinx\boards\" 
3. Open the Base System Builder again and then the board "Virtex 5 XUPV5-LX110T Evaluation Platform" should appear when you create a project. 

![](http://i.imgur.com/dpXnNDP.png)
