#

TESTS = bench bench0 bench1 \
        sky0a sky0b sky1 sky2 \
	cas_11271a cas_11271b \
        test1 test2 test3 test4 test5

#  example on Mac:
CASA  = /Applications/CASA.app/Contents/MacOS/casa
#  example on Linux if you used the install_casa script
CASA  = ../casa/casa-release-5.1.2-4.el7/bin/casa
#  example on Linux: (assuming it's in your $PATH - the portable solution)
CASA  = casa

help:
	@echo tests = $(TESTS)

.PHONY: $(TESTS)

bench:
	@echo running bench.py ...
	time $(CASA) --nogui -c bench.py > bench.log 2>&1
	tail -4 bench.log

benchplot:
	@echo running bench.py ...
	time $(CASA) --nogui -c bench.py alma=1 plot=1 > bench.log 2>&1
	tail -4 bench.log

bench0:
	@echo running bench0.py ...
	time $(CASA) --nogui -c bench0.py > bench0.log 2>&1
	tail -8 bench0.log

bench1:
	@echo running bench1.py ...
	time $(CASA) --nogui -c bench1.py > bench1.log 2>&1
	tail -8 bench1.log

sky1:
	@echo running sky1.py ...
	time $(CASA) --nogui -c sky1.py > sky1.log 2>&1
	cp sky1.py sky1.log sky1
	tail -20 sky1.log

#  sky2 is the generic TP2VIS-only mapping testsuite, the "sky2_all" runs a variety of tests
sky2:
	@echo running sky2.py ...
	time $(CASA) --nogui -c sky2.py > sky2.log 2>&1
	cp sky2.py sky2.log sky2.ptg sky2
	tail -20 sky2.log

#  all the sky2 based simulations, I'm not adding these to the earlier TESTS=
SKY2_ALL = sky2_1 sky2_2 sky2_3 sky2_4 sky2_5 \
	   sky2_1a sky2_1b sky2_1c sky2_1d sky2_1e sky2_1f \
	   sky2_2a sky2_2b sky2_2c sky2_2d sky2_2e sky2_2f

sky2_all: $(SKY2_ALL)

sky2_all_clean:
	rm -rf $(SKY2_ALL)

sky2_all_tar:
	tar cf sky2_all.tar $(SKY2_ALL)

# flux as function of pixel size
sky2_1:
	# 200" sky, 50" beam
	time $(CASA) --nogui -c sky2.py pdir='"sky2_1"' pixel_m=0.05 pixel_s=0.8  > sky2_1.log 2>&1
	cp sky2.py sky2_1.log sky2_1.ptg sky2_1
	tail -20 sky2_1.log

sky2_2:
	# 400" sky
	time $(CASA) --nogui -c sky2.py pdir='"sky2_2"' pixel_m=0.1 pixel_s=1.6  > sky2_2.log 2>&1
	cp sky2.py sky2_2.log sky2_2.ptg sky2_2
	tail -20 sky2_2.log

sky2_3:
	# 800" sky
	time $(CASA) --nogui -c sky2.py pdir='"sky2_3"' pixel_m=0.2 pixel_s=3.2  > sky2_3.log 2>&1
	cp sky2.py sky2_3.log sky2_3.ptg sky2_3
	tail -20 sky2_3.log

sky2_4:
	# 1600" sky
	time $(CASA) --nogui -c sky2.py pdir='"sky2_4"' pixel_m=0.4 imsize_s=512 pixel_s=3.2  > sky2_4.log 2>&1
	cp sky2.py sky2_4.log sky2_4.ptg sky2_4
	tail -20 sky2_4.log

sky2_5:
	# 1600" sky
	time $(CASA) --nogui -c sky2.py pdir='"sky2_5"' pixel_m=0.4 pixel_s=6.4  > sky2_5.log 2>&1
	cp sky2.py sky2_5.log sky2_5.ptg sky2_5
	tail -20 sky2_5.log

# the flux loss in sky2_1,2,3,4/5 is due to large pixel size? Here in 20,30,40 we keep the pixel size (pixel_s) the same
sky2_20:
	# 400" sky
	time $(CASA) --nogui -c sky2.py pdir='"sky2_20"' pixel_m=0.1 imsize_s=512 > sky2_20.log 2>&1
	cp sky2.py sky2_20.log sky2_20.ptg sky2_20
	tail -20 sky2_20.log

sky2_30:
	# 800" sky
	time $(CASA) --nogui -c sky2.py pdir='"sky2_30"' pixel_m=0.2 imsize_s=1024  > sky2_30.log 2>&1
	cp sky2.py sky2_30.log sky2_30.ptg sky2_30
	tail -20 sky2_30.log

sky2_40:
	# 1600" sky
	time $(CASA) --nogui -c sky2.py pdir='"sky2_40"' pixel_m=0.4 imsize_s=2048  > sky2_40.log 2>&1
	cp sky2.py sky2_40.log sky2_40.ptg sky2_40
	tail -20 sky2_40.log

# flux as function of small gridding step
sky2_2a:
	# 400" sky
	time $(CASA) --nogui -c sky2.py pdir='"sky2_2a"' pixel_m=0.1 pixel_s=1.6 grid=25 > sky2_2a.log 2>&1
	cp sky2.py sky2_2a.log sky2_2a.ptg sky2_2a
	tail -20 sky2_2a.log

sky2_2b:
	# 400" sky
	time $(CASA) --nogui -c sky2.py pdir='"sky2_2b"' pixel_m=0.1 pixel_s=1.6 grid=20 > sky2_2b.log 2>&1
	cp sky2.py sky2_2b.log sky2_2b.ptg sky2_2b
	tail -20 sky2_2b.log

sky2_2c:
	# 400" sky
	time $(CASA) --nogui -c sky2.py pdir='"sky2_2c"' pixel_m=0.1 pixel_s=1.6 grid=15 > sky2_2c.log 2>&1
	cp sky2.py sky2_2c.log sky2_2c.ptg sky2_2c
	tail -20 sky2_2c.log

# bigger gridding steps to see the beam problem
sky2_2d:
	# 400" sky
	time $(CASA) --nogui -c sky2.py pdir='"sky2_2d"' pixel_m=0.1 pixel_s=1.6 grid=60 > sky2_2d.log 2>&1
	cp sky2.py sky2_2d.log sky2_2d.ptg sky2_2d
	tail -20 sky2_2d.log

sky2_2e:
	# 400" sky
	time $(CASA) --nogui -c sky2.py pdir='"sky2_2e"' pixel_m=0.1 pixel_s=1.6 grid=120 > sky2_2e.log 2>&1
	cp sky2.py sky2_2e.log sky2_2e.ptg sky2_2e
	tail -20 sky2_2e.log

sky2_2f:
	# 400" sky
	time $(CASA) --nogui -c sky2.py pdir='"sky2_2f"' pixel_m=0.1 pixel_s=1.6 grid=180 > sky2_2f.log 2>&1
	cp sky2.py sky2_2f.log sky2_2f.ptg sky2_2f
	tail -20 sky2_2f.log


# dscale range
sky2_1a:
	# 200" sky, 30" beam
	time $(CASA) --nogui -c sky2.py pdir='"sky2_1a"' pixel_m=0.05 pixel_s=0.8 dscale=2 > sky2_1a.log 2>&1
	cp sky2.py sky2_1a.log sky2_1a.ptg sky2_1a
	tail -20 sky2_1a.log

sky2_1b:
	# 200" sky, 15" beam
	time $(CASA) --nogui -c sky2.py pdir='"sky2_1b"' pixel_m=0.05 pixel_s=0.8 dscale=4 > sky2_1b.log 2>&1
	cp sky2.py sky2_1b.log sky2_1b.ptg sky2_1b
	tail -20 sky2_1b.log

sky2_1c:
	# 200" sky, 8" beam
	time $(CASA) --nogui -c sky2.py pdir='"sky2_1c"' pixel_m=0.05 pixel_s=0.8 dscale=8 > sky2_1c.log 2>&1
	cp sky2.py sky2_1c.log sky2_1c.ptg sky2_1c
	tail -20 sky2_1c.log

# bigger gridding step and the dish3 usage
sky2_1d:
	# 200" sky, 60" beam
	time $(CASA) --nogui -c sky2.py pdir='"sky2_1d"' dish=12 maxuv=12 dish3=12 > sky2_1d.log 2>&1
	cp sky2.py sky2_1d.log sky2_1d.ptg sky2_1d
	tail -20 sky2_1d.log

sky2_1e:
	# 200" sky, 30" beam
	time $(CASA) --nogui -c sky2.py pdir='"sky2_1e"' dish=24 maxuv=24 dish3=12 > sky2_1e.log 2>&1
	cp sky2.py sky2_1e.log sky2_1e.ptg sky2_1e
	tail -20 sky2_1e.log

sky2_1f:
	# 200" sky, 15" beam
	time $(CASA) --nogui -c sky2.py pdir='"sky2_1f"' dish=48 maxuv=48 dish3=12 > sky2_1f.log 2>&1
	cp sky2.py sky2_1f.log sky2_1f.ptg sky2_1f
	tail -20 sky2_1f.log

# varying dish, fixed dish3 with the same resolution?
sky2_1g:
	time $(CASA) --nogui -c sky2.py pdir='"sky2_1g"' dish=48 dish3=12 maxuv=10 > sky2_1g.log 2>&1
	cp sky2.py sky2_1g.log sky2_1g.ptg sky2_1g
	tail -20 sky2_1g.log

sky2_1h:
	time $(CASA) --nogui -c sky2.py pdir='"sky2_1h"' dish=48 dish3=24 maxuv=20 > sky2_1h.log 2>&1
	cp sky2.py sky2_1h.log sky2_1h.ptg sky2_1h
	tail -20 sky2_1h.log

sky2_1i:
	time $(CASA) --nogui -c sky2.py pdir='"sky2_1i"' dish=48 dish3=48 maxuv=40 > sky2_1i.log 2>&1
	cp sky2.py sky2_1i.log sky2_1i.ptg sky2_1i
	tail -20 sky2_1i.log



# older version of cas_11271
sky0:   sky0a sky0b
	@echo vi1 results:
	grep QAC_STATS sky0a.log
	@echo vi2 results:
	grep QAC_STATS sky0b.log

sky0a:
	VI1=1 $(CASA) --nogui -c sky0.py test='"sky0a"' > sky0a.log 2>&1

sky0b:
	$(CASA)       --nogui -c sky0.py test='"sky0b"' > sky0b.log 2>&1


# this will show that Amp(uv=0,0) is indeed approaches the full flux, 113100.572
sky2_000:
	time $(CASA) --nogui -c sky2.py pdir='"sky2_000"' pixel_m=0.005 grid=0 clean=0 > sky2_000.log 2>&1
	grep ^AMP sky2_000.log

# sky2 with a hole in the UV distribution
sky2_uvmin: sky2_uvmin1 sky2_uvmin2 sky2_uvmin4 sky2_uvmin6

sky2_uvmin1:
	time $(CASA) --nogui -c sky2.py pdir='"sky2_uvmin1"'  minuv=1 > sky2_uvmin1.log  2>&1

pjt:
	time $(CASA) --nogui -c sky2.py pdir='"sky2_uvmin1a"' minuv=1 > sky2_uvmin1a.log grid=25 >&1
	time $(CASA) --nogui -c sky2.py pdir='"sky2_uvmin1b"' minuv=1 > sky2_uvmin1b.log grid=20 >&1
	time $(CASA) --nogui -c sky2.py pdir='"sky2_uvmin1c"'  minuv=1 > sky2_uvmin1c.log niter='range(0,5000,500)' 2>&1
	time $(CASA) --nogui -c sky2.py pdir='"sky2_uvmin1d"'  minuv=1 > sky2_uvmin1d.log grid=15 dish=24 maxuv=24 niter='range(0,5000,500)' 2>&1
	time $(CASA) --nogui -c sky2.py pdir='"sky2_uvmin1e"'  minuv=2 > sky2_uvmin1e.log grid=15 dish=24 maxuv=24 niter='range(0,5000,500)' 2>&1
	time $(CASA) --nogui -c sky2.py pdir='"sky2_uvmin1f"'  minuv=1 > sky2_uvmin1f.log grid=22 dish=18 maxuv=18 niter='range(0,5000,500)' 2>&1

sky2_uvmin2:
	time $(CASA) --nogui -c sky2.py pdir='"sky2_uvmin2"' minuv=2 > sky2_uvmin2.log 2>&1
sky2_uvmin4:
	time $(CASA) --nogui -c sky2.py pdir='"sky2_uvmin4"' minuv=4 > sky2_uvmin4.log 2>&1
sky2_uvmin6:
	time $(CASA) --nogui -c sky2.py pdir='"sky2_uvmin6"'  minuv=6          > sky2_uvmin6.log 2>&1
	time $(CASA) --nogui -c sky2.py pdir='"sky2_uvmin6a"' minuv=6 maxuv=10 > sky2_uvmin6a.log 2>&1

# expose the mosaicing flux bug in CASA 5.1 (April 2018) - gridder='standard'  is not affected
cas_11271: cas_11271a cas_11271b
	@grep ^CASA cas_11271a.log
	@echo vi1 results:
	grep QAC_STATS cas_11271a.log
	@echo vi2 results:
	grep QAC_STATS cas_11271b.log


cas_11271a:
	VI1=1 $(CASA) --nogui -c cas_11271.py pdir='"cas_11271a"' > cas_11271a.log 2>&1
	cp cas_11271.py cas_11271a

cas_11271b:
	$(CASA)       --nogui -c cas_11271.py pdir='"cas_11271b"' > cas_11271b.log 2>&1
	cp cas_11271.py cas_11271b

#
test1:
	@echo running test1.py ...
	rm -fr test1
	time $(CASA) --nogui -c test1.py > test1.log 2>&1
	tail -8 test1.log

test2:
	@echo running test2.py ...
	rm -fr test2
	time $(CASA) --nogui -c test2.py > test2.log 2>&1
	tail -8 test2.log

test3:
	@echo running test3.py ...
	rm -fr test3
	time $(CASA) --nogui -c test3.py > test3.log 2>&1
	tail -8 test3.log

test4:
	export VI1=1
	@echo running test4.py ...
	rm -fr test4
	time $(CASA) --nogui -c test4.py > test4.log 2>&1
	tail -8 test4.log

test5:
	@echo running test5.py ...
	rm -fr test5
	time $(CASA) --nogui -c test5.py > test5.log 2>&1
	tail -8 test5.log
