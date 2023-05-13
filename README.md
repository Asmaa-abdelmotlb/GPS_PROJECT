# GPS_PROJECT

float ToRad(float angle){
	int degree = (int)angle/100;
	float minutes = angle - (float)degree*100;
	return ((degree+(minutes/60)) * (PI/180));
}

float GPS_getDistance(float cuurentLong, float currentLat, float destLong, float destLat){
	//Get Radian Angle
	float cuurentLongRad = ToRad(cuurentLong);
	float currentLatRad  = ToRad(currentLat);
	float destLongRad    = ToRad(destLong);
	float destLatRad     = ToRad(destLat);
	
	//Get difference
	float longdiff = destLongRad - cuurentLongRad;
	float latdiff  = destLatRad  - currentLatRad;
	
	//Calculate distance
	float a = pow(sin(latdiff/2),2) + cos(currentLatRad)*cos(destLatRad)*pow(sin(longdiff/2),2);
	double c = 2 * atan2(sqrt(a),sqrt(a-1));
	return Earth_Radius * c ;
}
