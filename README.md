# Make calibration .calib3 file using calib3.m
	.set correct z-steps
	.z [nm], wx, wy
	.cut off bad zones

# Make .raw file with imagej

# Reconstruct .raw file with WoehrLok and create .rawlocs

# Driftcorrect .rawlocs using DCN
	.save driftfile
	.dx [px], dy [px]

# Identify interesting ROI using DCN
	.note: xmin, xmax, ymin, ymax
	.large ROI with multiple structures for cross-correlation 
	.small ROI with structure of interest

# open .rawlocs, drift and calib3 in lok3.m and create .lok3
	.Enter REG information if applicable
	.transform pixel units to absolute nm
	.t [frame], x [nm], y [nm], z [nm], wx, wy, z [nm], ?
		

# open .lok3 in reconPNG.m to create XY, XZ .png

# open XY.png of two 'colors' with xcorr.m to create REG.txt
	.x [nm], y [nm]

# open small ROI in lok3.m again and apply registration.

# convert .lok3 into VISP format usinglok3_VISP.m creating VISp3D.txts
