# GPS_PROJECT

#include <math.h>
#include <string.h>
#include <stdlib.h>
#define PI 3.141592654
double const raduis_of_earth = 6371000; // 6371 in kilometers

// to convert the lattitudes and the longitudes to degree
float to_degree (float angle)
{
	int degree = (int) angle /100 ;
	float minutes= angle - (float)degree*100;
	degree= degree +(minutes /60 );
	return (degree);
	
}
 // to convert the lattitudes and the longitudes from degree to radian 
float degree_to_radian (float angle)
{
  double constant =PI /180 ;
	float rad_angle =angle* constant ;
	
	return rad_angle;
}


// to get distance between 2 points on a shphere whose raduis is the earth raduis 

float cal_distance (float lat_a_old,float lat_b_old,float long_a_old,float long_b_old)
{
	// declaration of the final modification of the latt and long 
float lat_a  = degree_to_radian(to_degree(lat_a_old));
float lat_b  = degree_to_radian(to_degree(lat_b_old));
float long_a = degree_to_radian(to_degree(long_a_old));
float long_b = degree_to_radian(to_degree(long_b_old));
	
	// declaration of the lattitude and longitude of the 2 points
float diff_lat = (lat_b - lat_a)/2;
float diff_long = (long_b - long_a)/2;

	// the mathematical function
float a= pow (sin (diff_lat),2)	+ cos (lat_a)* cos (lat_b)* pow(sin (diff_long),2);
float c= 2* atan2( sqrt(a),sqrt(1-a));
float d;
d= c*	raduis_of_earth ;
return (d); // this is the total distance covered 
	
	
	
}
