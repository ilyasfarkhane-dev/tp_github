'use client';

import { useState, useEffect } from 'react';
import { Card, CardHeader } from '@/components/ui/card';
import { Badge } from '@/components/ui/badge';
import { Input } from '@/components/ui/input';
import { Button } from '@/components/ui/button';
import { Dialog, DialogContent, DialogHeader, DialogTitle, DialogFooter } from '@/components/ui/dialog';
import { toast } from 'react-hot-toast'; // Import toast
import axiosInstance from '@/lib/apiClient';
import { jsPDF } from 'jspdf';

interface User {
  name: string;
  email: string;
}

interface Room {
  id: number;
  image: string;
  numero: string;
  price: number;
  description: string;
}

interface Technician {
  id: number;
  name: string;
  email: string;
  speciality: string;
}

interface Incident {
  id: number;
  description: string;
  status: string;
  technician: Technician | null;
  room: Room;
}

interface Reservation {
  id: number;
  room: Room;
  statusReservation: string;
  payementStatus: string;
}

export default function ProfilePage() {
  const [user, setUser] = useState<User>({ name: '', email: '' });
  const [reservations, setReservations] = useState<Reservation[]>([]);
  const [incidents, setIncidents] = useState<Incident[]>([]);
  const [roomId, setRoomId] = useState<number | null>(null);
  const [resId, setResId] = useState<number | null>(null);
  const [loading, setLoading] = useState<boolean>(true);
  const [error, setError] = useState<string | null>(null);
  const [incidentDescription, setIncidentDescription] = useState<string>('');
  const [isIncidentDialogOpen, setIsIncidentDialogOpen] = useState<boolean>(false);
  const [isPaymentDialogOpen, setIsPaymentDialogOpen] = useState<boolean>(false);
  const [email, setEmail] = useState<string>('');

  useEffect(() => {
    const fetchData = async () => {
      try {
        const profileResponse = await axiosInstance.get('/api/v1/auth/my-profile');
        setUser(profileResponse.data);

        const reservationResponse = await axiosInstance.get<Reservation[]>('/reservations/my-reservations');
        setReservations(reservationResponse.data);

        const incidentResponse = await axiosInstance.get<Incident[]>('/api/incidents/my-incidents');
        setIncidents(incidentResponse.data);
      } catch (err) {
        setError('Failed to fetch data');
      } finally {
        setLoading(false);
      }
    };

    fetchData();
  }, []);

  const handleSubmitIncident = async () => {
    if (!roomId) return;
    try {
      const response = await axiosInstance.post(`/api/incidents/create/${roomId}`, {
        description: incidentDescription,
      });
      setIncidents((prev) => [...prev, response.data]);
      setIsIncidentDialogOpen(false);
      setIncidentDescription('');
      toast.success('Your incident declaration submitted successfully!'); // Show success toast
    } catch (error) {
      console.error('Failed to submit incident:', error);
      toast.error('Failed to declare incident. Please try again.'); // Show error toast
    }
  };

  const generateRecu = (reservation: Reservation) => {
    const doc = new jsPDF();
  
    // Add a border box for better visual structure
    doc.setDrawColor(0);
    doc.setLineWidth(0.5);
    doc.rect(10, 10, 190, 277); // Outer border
  
    // Add logo at the top-left corner
    const logoUrl = "/image.png"; // Replace with your logo URL or base64 string
    doc.addImage(logoUrl, "PNG", 15, 15, 30, 30); // Adjust size and position
  
    // Header Section
    doc.setFontSize(18);
    doc.setFont("helvetica", "bold");
    doc.text("Receipt", 105, 30, { align: "center" });
  
    doc.setFontSize(12);
    doc.setFont("helvetica", "italic");
    doc.text("Thank you for staying with us!", 105, 38, { align: "center" });
  
    // Add a decorative line below the header
    doc.setDrawColor(150);
    doc.line(20, 50, 190, 50);
  
    // Body Section
    doc.setFontSize(14);
    doc.setFont("helvetica", "bold");
    doc.text("Receipt Details", 20, 65);
  
    doc.setFontSize(12);
    doc.setFont("helvetica", "normal");
    doc.text(`Room Number: ${reservation.room.numero}`, 20, 75);
    doc.text(`Resident Name: ${user.name}`, 20, 85);
    doc.text(`Email: ${user.email}`, 20, 95);
    doc.text(`Price: ${reservation.room.price.toFixed(2)} USD`, 20, 105);
  
    // Add a dashed separator for visual clarity
    doc.setDrawColor(200);
    doc.setLineDashPattern([3, 3]);
    doc.line(20, 115, 190, 115);
  
    // Footer Section
    doc.setFontSize(14);
    doc.setFont("helvetica", "bold");
    doc.text("Contact Information", 20, 130);
  
    doc.setFontSize(12);
    doc.setFont("helvetica", "normal");
    doc.text("Support Email: LuxStay@support.com", 20, 140);
    doc.text("Phone: +123 456 7890", 20, 150);
  
    // Footer Note
    doc.setFont("helvetica", "italic");
    doc.setFontSize(10);
    doc.setTextColor(100);
    doc.text(
      "This receipt is generated automatically. Please retain it for your records.",
      20,
      165
    );
  
    // Save the PDF
    doc.save(`receipt_room_${reservation.room.numero}.pdf`);
    toast.success("Receipt generated successfully!");
  };
  
  
  
  const handleSubmitPayment = async () => {
    if (!email || !resId) return;
    try {
      await axiosInstance.put(`/reservations/${resId}/pay`);
      setReservations((prev) =>
        prev.map((res) => (res.id === resId ? { ...res, payementStatus: 'PAID' } : res))
      );
      setIsPaymentDialogOpen(false);
      setEmail('');
      toast.success('Your payment submitted successfully!');
    } catch (error) {
      console.error('Failed to submit payment:', error);
      toast.error('Failed to submit your payment. Please try again.');
    }
  };

  const getBadgeColor = (status: string) => {
    switch (status) {
      case 'ACCEPTED':
        return 'bg-green-500';
      case 'DECLINED':
        return 'bg-red-500';
      case 'PENDING':
        return 'bg-yellow-500';
      default:
        return 'bg-gray-500';
    }
  };

  if (loading) return <div>Loading...</div>;
  if (error) return <div className="text-red-500">{error}</div>;

  return (
    <div className="w-full flex flex-col items-center py-40 px-16 space-y-8">
      <Card className="max-w-4xl w-full">
        <CardHeader className="flex flex-col items-center text-center">
          <h3 className="text-xl font-semibold">{user.name}</h3>
          <Badge className="bg-blue-500 mt-2">Verified</Badge>
        </CardHeader>
        <div className="p-4">
          <label className="text-sm font-medium">Email</label>
          <Input value={user.email} disabled className="mt-2" />
        </div>
      </Card>

      <Card className="max-w-4xl w-full">
        <CardHeader>
          <h3 className="text-lg font-semibold">My Rooms</h3>
        </CardHeader>
        <div className="p-4 space-y-4">
          {reservations.map((reservation) => (
            <div key={reservation.id} className="flex items-center justify-between border-b pb-4 mb-4">
              <img
                src={reservation.room.image}
                alt={`Room ${reservation.room.numero}`}
                className="w-16 h-16 rounded-lg"
              />
              <div>
                <h4 className="text-md font-medium">Room {reservation.room.numero}</h4>
                <Badge className={getBadgeColor(reservation.statusReservation)}>
                  {reservation.statusReservation}
                </Badge>
              </div>
              <div className="flex gap-2">
                <Button onClick={() => {
                  setRoomId(reservation.room.id);
                  setIsIncidentDialogOpen(true);
                }}>Declare Incident</Button>
                <Button
                  className={reservation.payementStatus === 'PAID' ? 'bg-green-500' : 'bg-yellow-500'}
                  onClick={() => {
                    setResId(reservation.id);
                    setIsPaymentDialogOpen(true);
                  }}
                >
                  {reservation.payementStatus === 'PAID' ? 'Paid' : 'Pay'}
                </Button>
                {reservation.payementStatus === 'PAID' && (
                  <Button onClick={() => generateRecu(reservation)}>Recu</Button>
                )}
                
              </div>
            </div>
          ))}
        </div>
      </Card>

      {/* Incidents Table Section */}
      <div className="space-y-8 p-8">
        <h2 className="text-2xl font-semibold text-gray-800">My Incidents</h2>
        {incidents.length === 0 ? (
          <p className="text-center text-gray-600">No incidents found</p>
        ) : (
          <div className="overflow-x-auto mt-4">
            <table className="min-w-full table-auto bg-white shadow-md rounded-lg">
              <thead className="bg-gray-100">
                <tr>
                  <th className="py-3 px-4 text-left text-sm font-medium text-gray-600">Description</th>
                  <th className="py-3 px-4 text-left text-sm font-medium text-gray-600">Status</th>
                  <th className="py-3 px-4 text-left text-sm font-medium text-gray-600">Technician</th>
                  <th className="py-3 px-4 text-left text-sm font-medium text-gray-600">Speciality</th>
                </tr>
              </thead>
              <tbody>
                {incidents.map((incident) => (
                  <tr key={incident.id} className="border-b border-gray-200 hover:bg-gray-50">
                    <td className="py-3 px-4 text-sm text-gray-700">{incident.description}</td>
                    <td className="py-3 px-4 text-sm">
                      <span
                        className={`inline-block px-3 py-1 text-white text-sm rounded-full ${
                          incident.status === 'PENDING'
                            ? 'bg-yellow-400'
                            : incident.status === 'RESOLVED'
                            ? 'bg-green-500'
                            : incident.status === 'ONGOING'
                            ? 'bg-blue-500'
                            : 'bg-gray-500'
                        }`}
                      >
                        {incident.status}
                      </span>
                    </td>
                    <td className="py-3 px-4 text-sm text-gray-700">
                      {incident.technician ? (
                        <span className="font-semibold">{incident.technician.name}</span>
                      ) : (
                        <span className="text-gray-500">Not assigned yet</span>
                      )}
                    </td>
                    <td className="py-3 px-4 text-sm text-gray-700">
                      {incident.technician ? incident.technician.speciality : 'N/A'}
                    </td>
                  </tr>
                ))}
              </tbody>
            </table>
          </div>
        )}
      </div>


      {/* Dialogs */}
      <Dialog open={isIncidentDialogOpen} onOpenChange={setIsIncidentDialogOpen}>
        <DialogContent>
          <DialogHeader>
            <DialogTitle>Declare Incident</DialogTitle>
          </DialogHeader>
          <textarea
            className="w-full p-2 border rounded-md"
            placeholder="Describe the incident"
            value={incidentDescription}
            onChange={(e) => setIncidentDescription(e.target.value)}
          />
          <DialogFooter>
            <Button onClick={() => setIsIncidentDialogOpen(false)}>Cancel</Button>
            <Button onClick={handleSubmitIncident}>Submit</Button>
          </DialogFooter>
        </DialogContent>
      </Dialog>

      <Dialog open={isPaymentDialogOpen} onOpenChange={setIsPaymentDialogOpen}>
        <DialogContent>
          <DialogHeader>
            <DialogTitle>Payment</DialogTitle>
          </DialogHeader>
          <Input
            type="email"
            placeholder="Enter your email"
            value={email}
            onChange={(e) => setEmail(e.target.value)}
            className="w-full p-2 border rounded-md"
          />
          <DialogFooter>
            <Button onClick={() => setIsPaymentDialogOpen(false)}>Cancel</Button>
            <Button onClick={handleSubmitPayment}>Submit</Button>
          </DialogFooter>
        </DialogContent>
      </Dialog>
    </div>
  );
}
