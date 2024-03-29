#  Makefile for building executables on a UNIX System.

#SHAPEFILES includes all files in the shapefile library
SHAPEFILES = shapelib/dbfopen.o shapelib/safileio.o shapelib/shpopen.o \
             shapelib/shptree.o ReadOutlets.o
#OBJFILES includes classes, structures, and constants common to all files
OBJFILES = commonLib.o tiffIO.o
CONNECTDOWNFILES = connectdownmn.o connectdown.o $(OBJFILES) $(SHAPEFILES)
D8FILES = aread8mn.o aread8.o $(OBJFILES) $(SHAPEFILES)
DINFFILES = areadinfmn.o areadinf.o $(OBJFILES) $(SHAPEFILES)
D8 = D8FlowDirmn.o d8.o Node.o $(OBJFILES) $(SHAPEFILES)
D8DISTDOWN = D8DistDownToStream.o D8DistDownToStreammn.o  $(OBJFILES)
DINFDISTDOWN = DinfDistDown.o DinfDistDownmn.o $(OBJFILES)
DINFDISTUP = DinfDistUpToRidge.o DinfDistUpToRidgemn.o $(OBJFILES)
DINF = DinfFlowDirmn.o dinf.o Node.o  $(OBJFILES) $(SHAPEFILES)
DROPANALYSISFILES = DropAnalysis.o DropAnalysismn.o $(OBJFILES) $(SHAPEFILES)
MVOUTLETSTOSTRMFILES = MoveOutletsToStrm.o MoveOutletsToStrmmn.o $(OBJFILES) $(SHAPEFILES)
PITREMOVE = flood.o PitRemovemn.o $(OBJFILES)
THRESHOLD = Threshold.o Thresholdmn.o $(OBJFILES)
# added by Liangjun Zhu,  2015/5/22
CURVATURE = Curvature.o Curvaturemn.o $(OBJFILES)
D8DISTUP = D8DistUpToRidge.o D8DistUpToRidgemn.o $(OBJFILES)
FUZSLPPOSINF = FuzzySlpPosInference.o FuzzySlpPosInferencemn.o $(OBJFILES)
HARDENSLPPOS = HardenSlpPos.o HardenSlpPosmn.o $(OBJFILES)
TYPLOCSEL = stats.o SelectTypLocSlpPos.o SelectTypLocSlpPosmn.o $(OBJFILES)
CALCULATOR = SimpleCalculator.o SimpleCalculatormn.o $(OBJFILES)

#The following are compiler flags common to all building rules
# my laptop, ubuntu 14.04
#MPI_DIR = /usr/
# linux cluster in dgpm
ifndef MPI_DIR
	MPI_DIR = /home/zhulj/mpich/
endif
CC = $(MPI_DIR)bin/mpic++
CFLAGS=-O2
CFLAGS=-g -Wall
CFLAGS=-g -fopenmp -std=c++11
LARGEFILEFLAG= -D_FILE_OFFSET_BITS=64
INCDIRS=-I$(MPI_DIR)include
ifndef INSTALLDIR
	INSTALLDIR=/home/zhulj/AutoFuzSlpPos/exec
endif


#Rules: when and how to make a file

all : $(SHAPEFILES) $(INSTALLDIR)/aread8 $(INSTALLDIR)/areadinf $(INSTALLDIR)/connectdown $(INSTALLDIR)/d8flowdir $(INSTALLDIR)/d8distdowntostream $(INSTALLDIR)/dinfdistuptoridge $(INSTALLDIR)/dinfdistdown $(INSTALLDIR)/dinfflowdir $(INSTALLDIR)/dropanalysis $(INSTALLDIR)/moveoutletstostreams $(INSTALLDIR)/pitremove $(INSTALLDIR)/threshold $(INSTALLDIR)/curvature $(INSTALLDIR)/d8distuptoridge $(INSTALLDIR)/fuzzyslpposinference $(INSTALLDIR)/hardenslppos $(INSTALLDIR)/selecttyplocslppos $(INSTALLDIR)/simplecalculator clean 

$(INSTALLDIR)/aread8 : $(D8FILES)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(D8FILES) $(LDLIBS) $(LDFLAGS)

$(INSTALLDIR)/areadinf : $(DINFFILES)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(DINFFILES) $(LDLIBS) $(LDFLAGS)

$(INSTALLDIR)/connectdown : $(CONNECTDOWNFILES)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(CONNECTDOWNFILES) $(LDLIBS) $(LDFLAGS)
	
$(INSTALLDIR)/d8flowdir : $(D8)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(D8) $(LDLIBS) $(LDFLAGS)

$(INSTALLDIR)/d8distdowntostream : $(D8DISTDOWN)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(D8DISTDOWN) $(LDLIBS) $(LDFLAGS)

$(INSTALLDIR)/dinfdistuptoridge : $(DINFDISTUP)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(DINFDISTUP) $(LDLIBS) $(LDFLAGS)

$(INSTALLDIR)/dinfdistdown : $(DINFDISTDOWN)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(DINFDISTDOWN) $(LDLIBS) $(LDFLAGS)

$(INSTALLDIR)/dinfflowdir : $(DINF)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(DINF) $(LDLIBS) $(LDFLAGS) 

$(INSTALLDIR)/dropanalysis : $(DROPANALYSISFILES)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(DROPANALYSISFILES) $(LDLIBS) $(LDFLAGS)

$(INSTALLDIR)/moveoutletstostreams : $(MVOUTLETSTOSTRMFILES)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(MVOUTLETSTOSTRMFILES) $(LDLIBS) $(LDFLAGS)

$(INSTALLDIR)/pitremove : $(PITREMOVE)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(PITREMOVE) $(LDLIBS) $(LDFLAGS)

$(INSTALLDIR)/threshold : $(THRESHOLD)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(THRESHOLD) $(LDLIBS) $(LDFLAGS) 

$(INSTALLDIR)/curvature : $(CURVATURE)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(CURVATURE) $(LDLIBS) $(LDFLAGS)
$(INSTALLDIR)/d8distuptoridge : $(D8DISTUP)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(D8DISTUP) $(LDLIBS) $(LDFLAGS)
$(INSTALLDIR)/fuzzyslpposinference : $(FUZSLPPOSINF)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(FUZSLPPOSINF) $(LDLIBS) $(LDFLAGS)
$(INSTALLDIR)/hardenslppos : $(HARDENSLPPOS)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(HARDENSLPPOS) $(LDLIBS) $(LDFLAGS)
$(INSTALLDIR)/selecttyplocslppos : $(TYPLOCSEL)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(TYPLOCSEL) $(LDLIBS) $(LDFLAGS)
$(INSTALLDIR)/simplecalculator : $(CALCULATOR)
	$(CC) $(CFLAGS) -o $@ $(LIBDIRS) $(CALCULATOR) $(LDLIBS) $(LDFLAGS)

#Inference rule - states a general rule for compiling .o files
%.o : %.cpp
	$(CC) $(CFLAGS) $(INCDIRS) -c $<

.PHONY:clean
clean:
	rm *.o
	rm shapelib/*.o

